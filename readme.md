xmlrpc-message-umd
==================

**UNMAINTAINED** | This project is not maintained anymore (as of 2016 November 14).

[![NPM version](https://img.shields.io/npm/v/xmlrpc-message-umd.svg)](https://www.npmjs.com/package/xmlrpc-message-umd)
[![Dependency Status](https://img.shields.io/david/t1st3/xmlrpc-message-umd.svg)](https://david-dm.org/t1st3/xmlrpc-message-umd)
[![Build Status](https://img.shields.io/travis/t1st3/xmlrpc-message-umd.svg)](https://travis-ci.org/t1st3/xmlrpc-message-umd)


About
---

`xmlrpc-message-umd` is an XMLRPC message builder, written in Javascript. 

This module only provides a string builder; it does not make any HTTP request by itself. Basically, it is just a small set of utils that create a valid "ready-to-be-sent" XMLRPC string, also meaning it works with any HTTP request module.



Installation for production
---

**with Node.js**

`xmlrpc-message-umd` is available on [NPM](https://www.npmjs.com/package/xmlrpc-message-umd)

You can install it with the following command:

    npm install xmlrpc-message-umd


**Browser globals and AMD**


`xmlrpc-message-umd` is available on [Bower](http://bower.io/search/?q=xmlrpc-message-umd)

To install it from Bower, just run 

    bower install xmlrpc-message-umd




Installation for development
---


You also can download the whole project (and build it from its source; see below).

Either use `git clone` command to get it:

    git clone https://github.com/t1st3/xmlrpc-message-umd.git

Or download the latest version of [the whole project](https://github.com/t1st3/xmlrpc-message-umd/archive/master.zip).

Then, get the dependencies of the project from both Bower and NPM:

    npm install
    bower install


Usage
---

To create an XML-RPC message, just add parameters to a new instance of the lib, like the following:

```js

var a = ["chicken","duck","goose"];
var obj = new Object();
obj.x = 20;
obj.y = "cow";
obj.z = 3.14;
var date = new Date();
var msg = new XMLRPCMessage();
msg.setMethod("system.myMethod");
msg.addParameter("mississippi");
msg.addParameter(7);
msg.addParameter(false);
msg.addParameter(a);
msg.addParameter(obj);
msg.addParameter(date);
msg.xml();

```

`msg.xml()` would then return the complete XML string.


By default, the type of the parameters is automatically detected. You can prevent this behavior and force the type of a parameter, for example:

```js

var msg = new XMLRPCMessage();
msg.setMethod("system.myMethod");
msg.addParameter("qwerty", "base64");

```

As described on [Apache Sofftware Foundation's XMLRPC documentation](https://ws.apache.org/xmlrpc/types.html), the following types are available for XMLRPC:

* `i4` or `int`
* `boolean`
* `string`
* `double`
* `dateTime.iso8601`
* `base64`
* `struct`
* `array`


Finally, you can also force types of elements within a `struct` element or an `array` element:

```js

var obj = new Object();
obj.x = 20;
obj.y = {data: "cow", type: "base64"};
var msg = new XMLRPCMessage();
msg.setMethod("system.myMethod");
msg.addParameter(obj);

```



Build from source
---


First, see "Installation for development" above. 
Do not forget to get the dependencies!

Then, you also need to install [Gulp](http://gulpjs.com/) globally to build the project.

    npm install -g gulp

See more at the ["Getting started with Gulp" page](https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md#getting-started).

Once you got the dependencies and installed Gulp globally, to get info about the package from the command line, just run:

    gulp info


---

You are now ready to build!

The source is located in the "src" folder; the built target is located in the "dist" folder.

To build, just run:

    gulp build

---

**Tests**

To test, you can use either the `npm test` command or the `gulp test` command:

    npm test

or

    gulp test


---

**Serve and livereload**

You can also use the `serve` task to load the html pages from `./test/` in your browser.

    gulp serve

Once it has loaded the page in the browser, this task watches for any modification in the source.
If changes happen in the source, the task automatically reloads the page in the browser (livereload).



License
---


This piece of code is triple-licensed: [MIT / BSD / GPL licenses](https://github.com/t1st3/xmlrpc-message-umd/blob/master/license)



Initial author
---

[t1st3](https://github.com/t1st3/) 

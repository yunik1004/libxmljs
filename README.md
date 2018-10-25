# Libxmljs
[![Build Status](https://secure.travis-ci.org/yunik1004/libxmljs.svg?branch=build)](http://travis-ci.org/yunik1004/libxmljs)

[![AppVeyor Build status](https://ci.appveyor.com/api/projects/status/o443aft3q0ttqx4v/branch/build?svg=true)](https://ci.appveyor.com/project/yunik1004/libxmljs/branch/build)

> This is the updated version of znerol/libxmljs.

Main branches of this project are 'master' and 'build'.

To build this project, you have to run following commands:

```bash
$ git remote update
$ git remote add upstream https://github.com/libxmljs/libxmljs.git
$ git fetch upstream
$ git checkout -t origin/build
$ git merge upstream/master
```

After resolving conflict issues, you have to change the version number in package.json into the same value with upstream.

Next, run the following commands to push & build binary. Tag should be equal to v + version

```bash
$ git add .
$ git commit -m ""
$ git tag v0.19.5
$ git push origin build --tags
```

Finally, run the following commands to update the master branch.

```bash
$ git checkout master
$ git merge origin/build
```

After merging & resolving conflict issues, you have to change the binary remote_path in package.json file from libxmljs/libxmljs to yunik1004/libxmljs.

Then, run the following commands to push.

```bash
$ git add .
$ git commit -m ""
$ git push origin master
```

## Intro

LibXML bindings for [node.js](http://nodejs.org/)

```javascript
var libxmljs = require("libxmljs");
var xml =  '<?xml version="1.0" encoding="UTF-8"?>' +
           '<root>' +
               '<child foo="bar">' +
                   '<grandchild baz="fizbuzz">grandchild content</grandchild>' +
               '</child>' +
               '<sibling>with content!</sibling>' +
           '</root>';

var xmlDoc = libxmljs.parseXml(xml);

// xpath queries
var gchild = xmlDoc.get('//grandchild');

console.log(gchild.text());  // prints "grandchild content"

var children = xmlDoc.root().childNodes();
var child = children[0];

console.log(child.attr('foo').value()); // prints "bar"
```

## Support

* Docs - [http://github.com/libxmljs/libxmljs/wiki](http://github.com/libxmljs/libxmljs/wiki)
* Mailing list - [http://groups.google.com/group/libxmljs](http://groups.google.com/group/libxmljs)

## API and Examples

Check out the wiki [http://github.com/libxmljs/libxmljs/wiki](http://github.com/libxmljs/libxmljs/wiki).

See the [examples](https://github.com/libxmljs/libxmljs/tree/master/examples) folder.

## Installation via [npm](https://npmjs.org)

```shell
npm install libxmljs
```

## Contribute

Start by checking out the [open issues](https://github.com/libxmljs/libxmljs/issues?labels=&page=1&state=open). Specifically the [desired feature](https://github.com/libxmljs/libxmljs/issues?labels=desired+feature&page=1&state=open) ones.

### Requirements

Make sure you have met the requirements for [node-gyp](https://github.com/TooTallNate/node-gyp#installation). You DO NOT need to manually install node-gyp; it comes bundled with node.

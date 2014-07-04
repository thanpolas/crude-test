# crude-test

> API Test Helpers for [crude](https://github.com/thanpolas/crude).

[![Build Status](https://secure.travis-ci.org/thanpolas/crude-test.png?branch=master)](http://travis-ci.org/thanpolas/crude-test)

## Install

Install the module using NPM:

```
npm install crude-test --save
```

## <a name='TOC'>Table of Contents</a>

1. [Overview](#overview)
1. [API](#api)

## Overview

crude-test provides a convenient, fast and effective way to test your endpoints that were created using the [crude](https://github.com/thanpolas/crude) package. Usage is pretty straighforward:

```js
var CrudeTest = require('crude-test');

// load internal modules
var userFix = require('./fixtures/user.fix');
var UserEnt = require('./entities/user.ent');

// initialize the Crude tester
var crudeTest = new CrudeTest({
    endpoint: '/user',
    fixture: userFix.one,
    stringAttr: 'firstName',
    idAttr: '_id',
    uniqueAttr: 'email',
    Entity: UserEnt,
});

// run the tests
crudeTest.run();
```

## API

### Constructor

* `Object=` *optOptions* Optionally define a set of options.

The crude-test package exposes a constructor that you need to invoke with the `new` keyword.

```js
var CrudeTest = require('crude-test');

var crudeTest = new CrudeTest();
```

### setup(options)

* `Object` *options* A set of options

You may invoke `setup()` after the instanciation to configure the crude-test instance.

### Options

Find bellow all the available options to configure crude-test. In type definitions the `=` symbol means that the property is optional, all properties not having the equal symbol are REQUIRED:

    * *hostname* `string` The hostname to perform the tests against, i.e. `http://localhost:3000`.
    * *endpoint* `string` The endpoint to test, i.e. `/user`.
    * *fixture* `Object` the data fixture to use, provide a data object to use for creating items.
    * *stringAttr* `string` A string attribute in the fixture to use for updating and query filtering, any string type attribute will do.
    * *uniqueAttr* `string` An attribute that acts as a unique identifier of the record, e.g. the email if the model is a user, in an empty db this can be any field, not neccessarily an actually unique one.
    * *Entity* `Entity` The [entity instance](https://github.com/thanpolas/entity) of the model to be tested.
    * *create* `Object` Create OP related parameters:
        * *response* `Function` A node.js style callback with the tests res.
    * *readList* `Object` Read List OP related parameters:
        * *response* `Function` A node.js style callback with the tests res.
    * *readItem* `Object` Read Item OP related parameters:
        * *response* `Function` A node.js style callback with the tests res.
    * *readFilter* `Object` Read Filter OP related parameters:
        * *response* `Function` A node.js style callback with the tests res.
    * *update* `Object` Update OP related parameters:
        * *response* `Function` A node.js style callback with the tests res.
    * *delete* `Object` Delete OP related parameters:
        * *response* `Function` A node.js style callback with the tests res.

**[[⬆]](#TOC)**

## Release History

- **v0.0.1**, *04 Jul 2014*
    - Big Bang

## License

Copyright (c) 2014 Thanasis Polychronakis. Licensed under the MIT license.

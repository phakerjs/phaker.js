# phaker.js - generate massive amounts of fake data in the browser and node.js

A drop in replacement to faker.js say hello to **phaker.js**

![phaker.js logo](https://raw.githubusercontent.com/phakerjs/phaker.js/main/logo.png)

[![Build Status](https://img.shields.io/github/workflow/status/phakerjs/phaker.js/build-test/main)](https://github.com/phakerjs/phaker.js)
[![Coverage Status](https://coveralls.io/repos/github/phakerjs/phaker.js/badge.svg?branch=main)](https://coveralls.io/github/phakerjs/phaker.js?branch=main)
[![License](https://img.shields.io/npm/l/phaker.js)](https://www.npmjs.com/package/phaker.js)
[![Version](https://img.shields.io/npm/v/phaker.js)](https://www.npmjs.com/package/phaker.js)

## Why phaker?

On or about Jan 4th 2022, the original author of faker (Marak Squires) deleted the faker.js repo and published a v6.6.6 version that only contained a readme.

## Usage

### Browser

```html
<script src = "phaker.js" type = "text/javascript"></script>
<script>
  var randomName = faker.name.findName(); // Caitlyn Kerluke
  var randomEmail = faker.internet.email(); // Rusty@arne.info
  var randomCard = faker.helpers.createCard(); // random contact card containing many properties
</script>
```

### Node.js

```js
var faker = require('phaker.js');

var randomName = faker.name.findName(); // Rowan Nikolaus
var randomEmail = faker.internet.email(); // Kassandra.Haley@erich.biz
var randomCard = faker.helpers.createCard(); // random contact card containing many properties
```

## API

### JSDoc API Browser

[http://phakerjs.github.io/phaker.js/](http://phakerjs.github.io/phaker.js/)

### API Methods

{{{API}}}

### Faker.fake()

faker.js contains a super useful generator method `Faker.fake` for combining faker API methods using a mustache string format.

**Example:**

{{=<% %>=}}

``` js
console.log(faker.fake("{{name.lastName}}, {{name.firstName}} {{name.suffix}}"));
// outputs: "Marks, Dean Sr."
```

<%={{ }}=%>

This will interpolate the format string with the value of methods `name.lastName()`, `name.firstName()`, and `name.suffix()`

## Localization

As of version `v2.0.0` faker.js has support for multiple localities.

The default language locale is set to English.

Setting a new locale is simple:

```js
// sets locale to de
faker.locale = "de";
```

{{LOCALES}}

### Individual Localization Packages

faker.js supports incremental loading of locales.

By default, requiring `faker` will include *all* locale data.

In a production environment, you may only want to include the locale data for a specific set of locales.

```js
// loads only de locale
var faker = require('faker/locale/de');
```

## Setting a randomness seed

If you want consistent results, you can set your own seed:

```js
faker.seed(123);

var firstRandom = faker.random.number();

// Setting the seed again resets the sequence.
faker.seed(123);

var secondRandom = faker.random.number();

console.log(firstRandom === secondRandom);
```

## Tests

```shell
npm install .
make test
```

You can view a code coverage report generated in coverage/lcov-report/index.html.

## Building faker.js

faker uses [gulp](http://gulpjs.com/) to automate its build process. Each build operation is a separate task which can be run independently.

### Browser Bundle

```shell
npm run browser
```

### Building JSDocs

[JSDOC](https://jsdoc.app/) v3 HTML API documentation

```shell
npm run jsdoc
```

### Building ReadMe

The `ReadMe.md` file for `faker.js` is automatically generated and should not be modified directly. All updates to `ReadMe.md` should be performed in `./build/src/docs.md` and then the build script should be run.

```shell
npm run readme
```

## Version Release Schedule

faker.js is a popular project used by many organizations and individuals in production settings. Major and Minor version releases are generally on a monthly schedule. Bugs fixes are addressed by severity and fixed as soon as possible.

If you require the absolute latest version of `phaker.js` the `main` branch @ <http://github.com/phakerjs/phaker.js/> should always be up to date and working.

## Maintainers

* Kam Lasater (https://github.com/seekayel)

## License

* <https://github.com/marak/faker.js> - Copyright (c) {{startYear}}-{{currentYear}} Kam Lasater
* <https://github.com/marak/faker.js> - Copyright (c) 2010-2020 Marak Squires
* <https://github.com/stympy/faker/> - Copyright (c) 2007-2010 Benjamin Curtis
* <http://search.cpan.org/~jasonk/Data-Faker-0.07/> - Copyright 2004-2005 by Jason Kohles

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

# cta-common
[![Build Status](https://travis-ci.org/thomsonreuters/cta-common.svg?branch=master)](https://travis-ci.org/thomsonreuters/cta-common)
[![Coverage Status](https://coveralls.io/repos/github/thomsonreuters/cta-common/badge.svg?branch=master)](https://coveralls.io/github/thomsonreuters/cta-common?branch=master)
[![codecov](https://codecov.io/gh/thomsonreuters/cta-common/branch/master/graph/badge.svg)](https://codecov.io/gh/thomsonreuters/cta-common)

Common Modules for Compass Test Automation, One of Libraries in CTA-OSS Framework

## General Overview

### Overview

In cta-common, there are four modules as following:

1. [ConfigModule](#1-configmodule)
1. [LoaderModule](#2-loadermodule)
1. [RootModule](#3-rootmodule)
1. [ValidateModule](#4-validatemodule)

These modules providing common functions across CTA-OSS.

## Guidelines

We aim to give you brief guidelines here.

```javascript
const cta_common = require("cta-common");
```

### 1. ConfigModule

It loads the config for specified module using file structure: **[module_root]/lib/apps/main/config**.

```javascript
const moduleName = "sample-module";
const config = cta_common.config(moduleName);
```

The file, which locates at _sample-module/lib/apps/main/config/index.js_, is loaded as the **config**.

### 2. LoaderModule

It loads modules from all _*.js_ files in specified directory. Other extension files are excluded.

For example: there are three files in directory:  _**module1.js**_, _**module2.js**_, and _**module3.js**_


#### Output as Array

```javascript
const sampleDirectory = "sample-directory";
const array_output = cta_common.loader.asArray(sampleDirectory);
// array_output = [ {default_export_module1}, {default_export_module2}, {default_export_module3} ]
```

#### Output as Object

```javascript
const sampleDirectory = "sample-directory";
const object_output = cta_common.loader.asObject(sampleDirectory);
// object_output = {
//   module1: {default_export_module1},
//   module2: {default_export_module2},
//   module3: {default_export_module3},
// }
```

### 3. RootModule

It resolves the root directory of module.

```javascript
const moduleName = "samplemodule";
const root = cta_common.root(moduleName);
```

For example, *[executing_application]/node_modules/samplemodule*

### 4. ValidateModule

It validates the **input** against specified **pattern**.

```javascript
const input = { value: "sample input" };
const pattern = "object";

const output = cta_common.validate(input, pattern);
```

This module is used to validate a bridge and a tool in CTA-OSS.

## To Do

Plan for next release

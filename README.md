**NOTE** This package was modified from pixeldesu's original moduleRaid for compatibility with webpack v5 used in WhatsApp Web. No support will be given outside of anything strictly necessary to extract modules in WhatsApp Web.

<div align='center'>
  <img width=200px src='.github/logo.png?raw=true'>

  <h1>moduleRaid</h1>
  <p>moduleRaid is a utility to get modules from <code>webpackChunkbuild</code> functions embedded on WhatsApp Web. It also provides functions to search through returned modules.</p>
</div>

<h2 align='center'>Installation</h2>

You can get moduleRaid over npm

```
$ npm install @pedroslopez/moduleRaid
```

Or if you directly want to use it in the browser

```html
<script src="https://unpkg.com/@pedroslopez/moduleraid@latest/moduleraid.js"></script>
```

Alternatively, just copy the script from `moduleraid.js` and run it in a devtool console.

<h2 align='center'>Usage</h2>

### Preparation

Using `moduleRaid` as a module, simply require and execute it somewhere where it will end up as a public facing script

```js
const moduleRaid = require('moduleraid')

window.mR = moduleRaid()
```

If you a running the script from the console or loading it over a service like unpkg, no further need for preparations!

### The `moduleraid` object

Once `moduleRaid` is run or included on a page that includes a Webpack build (usually noted by a `webpackJsonp` function), it
will return a object, containing:

* `modules`: An object containing all modules we could get from Webpack
* `constructors`: An array containing all module constructor functions
* `get(id)`: Get the module from the specified `id`
* `findModule(query)`: Return the module that has `query` as a key in its exports
* `findFunction(query)`: Return functions that include `query` (`query` can be either a string or a function)

If you run the code in devtools or load it as external script from unpkg/etc. the `moduleRaid` object can be found in `window.mR` by default.

**Note:** If moduleRaid had to get modules through iteration, `constructors` will be empty and so `findFunction` will not work.

#### Debug Mode

If you call moduleRaid with an optional argument `true`, you will enable debug output. Debug output will show errors that are normally supressed.

In the version that is minified and you can't just add another argument easily, simply run `window.mRdebug = true` before adding the script and you should
be fine!

<h2 align='center'>License</h2>

moduleRaid is licensed under the MIT License

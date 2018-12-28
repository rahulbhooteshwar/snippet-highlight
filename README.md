# snippet-highlight

## A lightweight, easy-to-use and framework agnostic syntax highlighter for your code examples(snippets) in web applications

# Why another code highlighter?
> There are many syntax highlighters avaliable already but most of those are either complex to setup or front end framework specific. `snippet-highlight` is built using concepts of web components. You can use it everywhere, i.e. Angular, React, Vue, any framework, No Framework!

# Index
 * [Usage](#usage)
 * [Installation](#installation)
 * [Framework Integration](#framework-integration)
    * [No Framework or Any Framework](#no-framework-or-any-framework)
    * [Angular](#angular)
    * [React](#react)
    * [Vue](#vue)
 * [Properties](#properties)
 * [Supported Languages](#supported-languages)
 * [Demo](#demo)


# Usage
* Install/Include dependency (npm module or script)
* Add Selector and pass attributes in your HTML page

```javascript
  <snippet-highlight theme="dark" language="javascript" content="your code-snippet"/>
```
# Installation
1. Install as npm module
    ```
    npm i snippet-highlight
    ```
    OR

    ```
    yarn add snippet-highlight
    ```
2. Or, Include as script on your HTML page
    ```html
    <script src="https://unpkg.com/snippet-highlight/dist/snippet-highlight.js"></script>
    ```

# Framework Integration

# No Framework or Any Framework
* Include the script as shown [above](#installation)
* Use the selector as shown in [usage](#usage)

# Angular

Using `snippet-highlight` within an Angular CLI project is a two-step process. We need to:

1. Include the `CUSTOM_ELEMENTS_SCHEMA` in the modules that use the components
1. Call `defineCustomElements(window)` from `main.ts` (or some other appropriate place)

## Including the Custom Elements Schema

Including the `CUSTOM_ELEMENTS_SCHEMA` in the module allows the use of the web components in the HTML markup without the compiler producing errors. Here is an example of adding it to `AppModule`:

```tsx
import { CUSTOM_ELEMENTS_SCHEMA, NgModule } from '@angular/core';

@NgModule({
  schemas: [CUSTOM_ELEMENTS_SCHEMA],
})
export class AppModule {}
```

The `CUSTOM_ELEMENTS_SCHEMA` needs to be included in any module that uses custom elements.

## Calling defineCustomElements

`snippet-highlight` includes a main function that is used to load the components in the collection. That function is called `defineCustomElements()` and it needs to be called once during the bootstrapping of your application. One convenient place to do this is in `main.ts` as such:

```tsx
import { defineCustomElements } from 'snippet-highlight/dist/loader';

platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.log(err));
defineCustomElements(window);
```

# React
With an application built using the `create-react-app` script the easiest way to include the component library is to call `defineCustomElements(window)` from the `index.js` file.

```tsx
import { defineCustomElements } from 'snippet-highlight/dist/loader';
defineCustomElements(window);
  ```
# Vue
In order to use the custom element library within the Vue app, the application must be modified to define the custom elements and to inform the Vue compiler which elements to ignore during compilation. This can all be done within the `main.js` file. For example:

```tsx
import Vue from 'vue';
import App from './App.vue';
import { defineCustomElements } from 'snippet-highlight/dist/loader';

Vue.config.productionTip = false;
Vue.config.ignoredElements = [/snippet-\w*/];

defineCustomElements(window);

new Vue({
  render: h => h(App)
}).$mount('#app');
```



## Properties

<table border="1">
<thead>
  <td><strong>Attribute</strong></td>
  <td><strong>Type</strong></td>
  <td><strong>Possible Values</strong></td>
  <td><strong>Description</strong></td>
</thead>
<tr>
  <td>content</td>
  <td>string</td>
  <td>Any code snippet in any of the supported languages</td>
  <td>Code snippet to be highlighted</td>
</tr>
<tr>
  <td>language</td>
  <td>string</td>
  <td>Any supported Language (See the list below), html (default)</td>
  <td>e.g. html, xml, java, javascript, css etc</td>
</tr>
<tr>
  <td>theme</td>
  <td>string</td>
  <td>dark(default), light</td>
  <td>Look and feel of code snippet</td>
</tr>
</table>

## Supported Languages


> `clike`,  `ruby`, `crystal`,  `csharp`,  `dotnet`,  `markup-templating`,  `markup`,  `xml`,  `html`,  `mathml`,  `svg`,  `django`,  `jinja2`,  `javascript`,  `js`,  `csp`,  `css`,  `d`,  `dart`,  `diff`,  `docker`,  `dockerfile`,  `eiffel`,  `elixir`,  `elm`,  `erb`,  `erlang`,  `flow`,  `fortran`,  `fsharp`,  `gedcom`,  `gherkin`,  `git`,  `glsl`,  `go`,  `graphql`,  `groovy`,  `haml`,  `handlebars`,  `haskell`,  `haxe`,  `hpkp`,  `hsts`,  `http`,  `ichigojam`,  `icon`,  `inform7`,  `ini`,  `io`,  `j`,  `java`,  `jolie`,  `json`,  `jsonp`,  `jsx`,  `julia`,  `keyman`,  `kotlin`,  `latex`,  `less`,  `liquid`,  `lisp`,  `elisp`,  `emacs`,  `emacs-lisp`,  `livescript`,  `lolcode`,  `lua`,  `makefile`,  `markdown`,  `matlab`,  `mel`,  `mizar`,  `monkey`,  `n4js`,  `n4jsd`,  `nasm`,  `nginx`,  `nim`,  `nix`,  `nsis`,  `ocaml`,  `oz`,  `parigp`,  `parser`,  `pascal`,  `objectpascal`,  `perl`,  `php`,  `sql`,  `plsql`,  `powershell`,  `processing`,  `prolog`,  `properties`,  `protobuf`,  `pug`,  `puppet`,  `pure`,  `python`,  `q`,  `qore`,  `r`,  `reason`,  `renpy`,  `rest`,  `rip`,  `roboconf`,  `rust`,  `sas`,  `sass`,  `scala`,  `scheme`,  `scss`,  `smalltalk`,  `smarty`,  `soy`,  `stylus`,  `swift`,  `tap`,  `tcl`,  `textile`,  `tsx`,  `tt2`,  `twig`,  `typescript`,  `ts`,  `velocity`,  `verilog`,  `vhdl`,  `vim`,  `visual-basic`,  `vb`,  `wasm`,  `wiki`,  `xeora`,  `xeoracube`,  `xojo`,  `xquery`,  `yaml`

# Demo

## Dark Theme
![Dark Theme HTML](https://res.cloudinary.com/designu/image/upload/v1546001737/CD32853C_aepc2b.png "Dark Theme HTML")

## Light Theme
![Light Theme Groovy](https://res.cloudinary.com/designu/image/upload/v1546001847/8F82AC0D_hzxt3l.png "Light Theme Groovy")

# pev2

A VueJS component to show a graphical vizualization of a PostgreSQL execution plan.

## Usage

To use the explain vizualizer you can choose one of the following options:

### Dalibo service (recommended)

[explain.dalibo.com](https://explain.dalibo.com)

This service is provided by `Dalibo` and can help you to share your plans with
colleagues or customers.

### Portable (on a USB stick)

PEV2 can be run locally.

Simply download [pev2.tar.gz](https://github.com/dalibo/pev2/releases/latest),
extract the archive and open `index.html` in your favorite internet browser.

### Local installation using docker

See [CONTRIBUTING](https://github.com/dalibo/pev2/blob/master/CONTRIBUTING.md).

### Integrated in a web application

PEV2 can be integrated as a component in a web application.

Install it:

```
npm install pev2
```

Declare the `PEV2` component and use it:

```javascript
import pev2 from "pev2";

new Vue({
  el: "#app",
  data: function () {
    return {
      plan: plan,
      query: query,
    };
  },
  components: {
    pev2: pev2,
  },
});
```

Then add the `PEV2` component to your template:

```html
<div id="app">
  <pev2 :plan-source="plan" :plan-query="query"></pev2>
</div>
```

`PEV2` requires `Bootstrap (CSS)` and `FontAwesome` to work so don't forget to
add the following in you header (or load them with your favorite bundler).

```html
<link
  href="https://unpkg.com/bootstrap@4.5.0/dist/css/bootstrap.min.css"
  rel="stylesheet"
/>
<link
  href="https://unpkg.com/@fortawesome/fontawesome-free@5.13.0/css/all.css"
  rel="stylesheet"
/>
```

For a complete example, see [this codesandbox][codesandbox].

[pev]: https://github.com/AlexTatiyants/pev
[atatiyan]: https://github.com/AlexTatiyants
[codesandbox]: https://codesandbox.io/s/pev2-ry2dd
[demo]: https://dalibo.github.io/pev2
[explain.dali.bo]: https://explain.dalibo.com

### Custom theme using SCSS

```js
// index.js

// import component without styles
import Pev2 from "pev2/components/pev2.common";
```

```scss
// styles.scss

// add pev2 vendor styles
@import "~tippy.js/dist/tippy.css";
@import "~splitpanes/dist/splitpanes.css";

// use any theme from highlight.js
@import "~highlight.js/styles/github.css";

// import pev2 variables
@import "~pev2/scss/variables";

// redefine variables from '~pev2/scss/variables' file
$text-color: red;

// import the rest of pev2 scss styles
@import "~pev2/scss/pev2";
```

## Disclaimer

This project is a rewrite of the excellent [Postgres Explain Visualizer
(pev)][pev]. Kudos go to [Alex Tatiyants][atatiyan].

The [pev][pev] project was initialy written in early 2016 but seems to be
abandoned since then. There was no activity at all for more than 3 years and
counting though there are several issues open and relevant pull requests
pending.

The current project has several goals:

- isolate the plan view component and its dependencies in order to use it in
  any web app with for example the ability to load a plan without requiring
  any copy-paste from the user,
- make it work with recent version of JS frameworks,
- upgrade Bootstrap to a more recent version,
- use VueJS just for a matter of taste,
- maintain the project to match upgrades in PostgreSQL.

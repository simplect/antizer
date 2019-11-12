# net.ofnir/antizer

[![Clojars Project](https://img.shields.io/clojars/v/net.ofnir/antizer.svg)](https://clojars.org/net.ofnir/antizer)

## Disclaimer

This is a fork of [antizer](https://github.com/priornix/antizer), which
sadly seems abandoned.  This fork is maintained as far as it concerns
updating the antd versions and adding new upstream components, but all
the nice things like generated docs and examples are stripped out.  See
the original project for that.

## What is antizer

Antizer is a ClojureScript library implementing [Ant Design](https://ant.design/) React components for [Reagent](https://github.com/reagent-project/reagent) and [Rum](https://github.com/tonsky/rum).

Ant Design is an enterprise-class UI design language and React-based implementation with the following features:

* An enterprise-class UI design language for web applications.
* A set of high-quality React components out of the box.
* Extensive API documentation and examples.

## Usage

To use Antizer, add the following to your project.clj:

```clojure
[net.ofnir/antizer "3.24.3-0"]
```

You would also need to add the ClojureScript React library that you will be using.

For Reagent:
```clojure
[reagent "X.Y.Z"]
```

For Rum:
```clojure
[rum "X.Y.Z"]
```

It is also necessary to include the relevant Ant Design CSS stylesheet in your HTML page. There are two ways that the CSS files can be included:

1. Loading the CSS stylesheet from an external CDN:

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/antd/${antd_version}/antd.min.css">
```

where `${antd_version}` must be the same antd library version as the one that Antizer is being linked to.

2. Alternatively, the CSS stylesheet can be loaded from either of the following classpaths. This can be done via [Ring](https://github.com/ring-clojure/ring) library's [wrap-resource](https://ring-clojure.github.io/ring/ring.middleware.resource.html) function:

* `cljsjs/antd/development/antd.inc.css`
* `cljsjs/antd/production/antd.min.inc.css`

An example of how this can be done is provided by https://github.com/dfuenzalida/antizer-demo.

You can also follow the instructions for customization with LESS [here](https://ant.design/docs/react/customize-theme).

### Quick Example

For Reagent:
```clojure
(require '[antizer.reagent :as ant])
(require '[reagent.core :as r])

(defn click-me []
  [ant/button {:on-click #(ant/message-info "Hello Reagent!")} "Click me"])

(defn init! []
  (r/render [click-me] (.-body js/document)))
```

For Rum:
```clojure
(require '[antizer.rum :as ant])
(require '[rum.core :as rum])

(defn click-me []
  (ant/button {:on-click #(ant/message-info "Hello Rum!")} "Click me"))

(defn init! []
  (rum/mount (click-me) (.-body js/document)))
```

## License

Copyright © 2017 Michael Lim

Copyright © 2019 Christoph Frick ofnir.net

Licensed under Eclipse Public License (see LICENSE).

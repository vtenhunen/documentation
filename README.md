# EGI documentation

[![Build Status](https://travis-ci.org/EGI-Foundation/documentation.svg?branch=master)](https://travis-ci.org/EGI-Foundation/documentation)

Sources to build
[EGI documentation static pages](https://egi-foundation.github.io/).

- [Hugo](https://gohugo.io/) is used to build a static website.
- The theme [docsy](https://www.docsy.dev) is used.
- The static site is
  [deployed on GitHub](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
  using a dedicated
  [GitHub repository](https://github.com/EGI-Foundation/EGI-Foundation.github.io).

> If you are interested in contributing please check the
> [Contributing Guide](https://docs.egi.eu/about/contributing/).

### Requirements

- mdl
- hugo
- NodeJS
  - postcss-cli
  - autoprofixer

### Installing dependencies, building and testing

To install npm+nodejs please check the instructions at:
https://www.npmjs.com/get-npm

The rest of the tools can be installed as follows:

```console
gem install mdl
npm install postcss-cli@7.1.2
npm install autoprefixer@9.0
```

The supported Hugo version packages are available under the `binaries` folder.

To build the site, from the repository root

```console
git submodule update --init --recursive --depth 1
mdl -s relaxed -s style.rb -r ~MD002,~MD024 content/
./binaries/<platform>/hugo
```

To test your changes:

```console
./binaries/<platform>/hugo server -D
```

The website is available locally at: http://localhost:1313/

## Usage

Please refer to [Hugo documentation](https://gohugo.io/documentation/) and
[docdock theme documentation](https://docdock.netlify.com/).

### Updating the theme

To ease management the [docsy](https://www.docsy.dev/docs/getting-started/)
theme has been cloned as a git submodule.

Updating the submodule

```console
git submodule foreach git pull
git commit themes/docsy -m 'Update theme'
```

### Deploying to the EGI organisation pages

To speed up the travis run a binary version of Hugo (extended version) for Linux
64 bit is included in the repository under `binaries`. Updates can be downloaded
at https://github.com/gohugoio/hugo/releases.

Travis will automatically deploy a new version when a PR is merged to master.

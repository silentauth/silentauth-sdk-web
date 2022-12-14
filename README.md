# SilentAuth SDK for Mobile Web Applications

[![License][license-image]][license-url]

The Web SDK for SilentAuth providing helper functions to check whether the device is on a cellular data connection, and for requesting the SilentAuth check.

## Installation

### Via jsDelivr CDN

```html
<script src="https://cdn.jsdelivr.net/npm/@silentauth/silentauth-sdk-web/dist/silentauth-sdk.umd.js"></script>
```

### Via NPM

```sh
$ npm install @silentauth/silentauth-sdk-web
```

## Usage

### Via jsDelivr CDN

#### Reachability Check

```html
<script src="https://cdn.jsdelivr.net/npm/@silentauth/silentauth-sdk-web/dist/silentauth-sdk.umd.js"></script>
<script>
  silentauth.getReachability(url)
</script>
```

#### PhoneCheck

When installed via a CDN a `silentauth` global is installed.

```html
<script src="https://cdn.jsdelivr.net/npm/@silentauth/silentauth-sdk-web/dist/silentauth-sdk.umd.js"></script>
<script>
  silentauth.openCheckUrl(url, config)
</script>
```

### Via NPM

#### Reachability Check

```js
import silentauth from '@silentauth/silentauth-sdk-web'

silentauth.getReachability(url)
```

#### PhoneCheck

When installed via NPM the imported object exposes the `openCheckUrl` function.

```js
import silentauth from '@silentauth/silentauth-sdk-web'

silentauth.openCheckUrl(checkUrl, config)
```

### `openCheckUrl` Config

The `openCheckUrl` function takes an optional `config` Object argument:

```js
silentauth.openCheckUrl(url, config)
```

The configuration options are:

```js
{
  // whether debug information will be logged to the console.
  // Defaults to `false`
  debug: boolean,

  // "image" - a zero pixel image is dynamically added to the DOM for the check_url request
  // "window" - `window.open` is called to open the check_url in a new window
  // Defaults to "image".
  checkMethod: "image" | "window",

  // If `checkMethod` was set to `window` identifies the number of
  // milliseconds after which the opened window will be closed.
  // Defaults to 3000.
  windowCloseTimeout: Number,

  // It will run the device coverage check to determine
  // if the device is on a mobile IP
  // Defaults to true
  checkDeviceCoverage: boolean,

  // Depending on what PhoneCheck API version the check is created with.
  // Defaults to "v0.2"
  version: "v0.1" | "v0.2",
}
```

## Local development

You can run `npm run dev` that will open rollup with watch mode that will re-compile the SDK after every change.

In another terminal you can run `npm run serve` to open a test web page where you can test real phone checks if you have the node server running or you can simply check a PhoneCheck `check_url`.

## Releasing

1. Bump the version if required
2. Run `npm run changelog` to auto-update the `CHANGELOG.md` and manually edit to finesse
3. Commit the changes read for release: `git commit -m 'chore(release): v{version}`
4. Tag the release `git tag v{version}`
5. Push the tags `git push --follow-tags origin main`
6. Build the project with `npm run build`
6. Publish to NPM `npm publish --access public`

## License

[MIT](LICENSE)

## Meta

Distributed under the MIT license. See ``LICENSE`` for more information.

[https://github.com/silentauth](https://github.com/silentauth)

[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-url]: LICENSE

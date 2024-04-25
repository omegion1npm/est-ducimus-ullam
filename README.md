# @omegion1npm/est-ducimus-ullam <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

*Note*: This package is a fork of https://npmjs.com/through, and builds off of it.

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

Easy way to create a `Stream` that is both `readable` and `writable`.

* Pass in optional `write` and `end` methods.
* `through` takes care of pause/resume logic if you use `this.queue(data)` instead of `this.emit('data', data)`.
* Use `this.pause()` and `this.resume()` to manage flow.
* Check `this.paused` to see current flow state. (`write` always returns `!this.paused`).

This function is the basis for most of the synchronous streams in [event-stream](http://github.com/dominictarr/event-stream).

``` js
var through = require('@omegion1npm/est-ducimus-ullam')

through(function write(data) {
    this.queue(data) //data *must* not be null
  },
  function end () { //optional
    this.queue(null)
  })
```

Or, can also be used _without_ buffering on pause, use `this.emit('data', data)`,
and this.emit('end')

``` js
var through = require('@omegion1npm/est-ducimus-ullam')

through(function write(data) {
    this.emit('data', data)
    //this.pause()
  },
  function end () { //optional
    this.emit('end')
  })
```

## Extended Options

You will probably not need these 99% of the time.

### autoDestroy=false

By default, `through` emits close when the writable
and readable side of the stream has ended.
If that is not desired, set `autoDestroy=false`.

``` js
var through = require('@omegion1npm/est-ducimus-ullam')

//like this
var ts = through(write, end, {autoDestroy: false})
//or like this
var ts = through(write, end)
ts.autoDestroy = false
```

[package-url]: https://npmjs.org/package/@omegion1npm/est-ducimus-ullam
[npm-version-svg]: https://versionbadg.es/omegion1npm/est-ducimus-ullam.svg
[deps-svg]: https://david-dm.org/omegion1npm/est-ducimus-ullam.svg
[deps-url]: https://david-dm.org/omegion1npm/est-ducimus-ullam
[dev-deps-svg]: https://david-dm.org/omegion1npm/est-ducimus-ullam/dev-status.svg
[dev-deps-url]: https://david-dm.org/omegion1npm/est-ducimus-ullam#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@omegion1npm/est-ducimus-ullam.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@omegion1npm/est-ducimus-ullam.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@omegion1npm/est-ducimus-ullam.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@omegion1npm/est-ducimus-ullam
[codecov-image]: https://codecov.io/gh/omegion1npm/est-ducimus-ullam/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/omegion1npm/est-ducimus-ullam/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/omegion1npm/est-ducimus-ullam
[actions-url]: https://github.com/omegion1npm/est-ducimus-ullam/actions

<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# Variance

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> [Negative binomial][negative-binomial-distribution] distribution [variance][variance].

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

The [variance][variance] for a [negative binomial][negative-binomial-distribution] random variable is

<!-- <equation class="equation" label="eq:negative_binomial_variance" align="center" raw="\operatorname{Var}\left( X \right) = \frac{pr}{(1-p)^{2}}" alt="Variance for a negative binomial distribution."> -->

```math
\mathop{\mathrm{Var}}\left( X \right) = \frac{pr}{(1-p)^{2}}
```

<!-- <div class="equation" align="center" data-raw-text="\operatorname{Var}\left( X \right) = \frac{pr}{(1-p)^{2}}" data-equation="eq:negative_binomial_variance">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@51534079fef45e990850102147e8945fb023d1d0/lib/node_modules/@stdlib/stats/base/dists/negative-binomial/variance/docs/img/equation_negative_binomial_variance.svg" alt="Variance for a negative binomial distribution.">
    <br>
</div> -->

<!-- </equation> -->

where `r` is the number of successes until experiment is stopped and `p` is the success probability in each trial. The random variable `X` denotes the number of failures until the `r` success is reached.

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/stats-base-dists-negative-binomial-variance
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var variance = require( '@stdlib/stats-base-dists-negative-binomial-variance' );
```

#### variance( r, p )

Returns the [variance][variance] of a [negative binomial][negative-binomial-distribution] distribution with parameters `r` (number of successes until experiment is stopped) and `p` (success probability).

```javascript
var v = variance( 100, 0.2 );
// returns ~2000.0

v = variance( 50, 0.5 );
// returns 100.0
```

If provided `NaN` as any argument, the function returns `NaN`.

```javascript
var v = variance( NaN, 0.5 );
// returns NaN

v = variance( 20, NaN );
// returns NaN
```

If provided a `r` which is not a positive number, the function returns `NaN`.

```javascript
var v = variance( -2.0, 0.5 );
// returns NaN
```

If provided a success probability `p` outside of `[0,1]`, the function returns `NaN`.

```javascript
var v = variance( 20, -1.0 );
// returns NaN

v = variance( 20, 1.5 );
// returns NaN
```

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var randu = require( '@stdlib/random-base-randu' );
var variance = require( '@stdlib/stats-base-dists-negative-binomial-variance' );

var v;
var i;
var r;
var p;

for ( i = 0; i < 10; i++ ) {
    r = randu() * 100;
    p = randu();
    v = variance( r, p );
    console.log( 'r: %d, p: %d, Var(X;r,p): %d', r.toFixed( 4 ), p.toFixed( 4 ), v.toFixed( 4 ) );
}
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->

* * *

<section class="c">

## C APIs

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- C usage documentation. -->

<section class="usage">

### Usage

```c
#include "stdlib/stats/base/dists/negative-binomial/variance.h"
```

#### stdlib_base_dists_negative_binomial_variance( r, p )

Returns the variance of a negative binomial distribution with parameters `r` (number of successes until experiment is stopped) and `p` (success probability).

```c
double v = stdlib_base_dists_negative_binomial_variance( 100.0, 0.2 );
// returns ~2000.0
```

The function accepts the following arguments:

-   **r**: `[in] double` number of successes until experiment is stopped.
-   **p**: `[in] double` success probability.

```c
double stdlib_base_dists_negative_binomial_variance( const double r, const double p );
```

</section>

<!-- /.usage -->

<!-- C API usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- C API usage examples. -->

<section class="examples">

### Examples

```c
#include "stdlib/stats/base/dists/negative-binomial/variance.h"
#include <stdlib.h>
#include <stdio.h>

static double random_uniform( const double min, const double max ) {
    double v = (double)rand() / ( (double)RAND_MAX + 1.0 );
    return min + ( v*(max-min) );
}

int main( void ) {
    double r;
    double p;
    double v;
    int i;


    for ( i = 0; i < 10; i++ ) {
        r = random_uniform( -1.0, 100.0 );
        p = random_uniform( 0.0, 1.0 );
        v = stdlib_base_dists_negative_binomial_variance( r, p );
        printf( "r: %.4f, p: %.4f, Var(X;r,p): %.4f\n", r, p, v );
    }
}
```

</section>

<!-- /.examples -->

</section>

<!-- /.c -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-base-dists-negative-binomial-variance.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-base-dists-negative-binomial-variance

[test-image]: https://github.com/stdlib-js/stats-base-dists-negative-binomial-variance/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/stats-base-dists-negative-binomial-variance/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-base-dists-negative-binomial-variance/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-base-dists-negative-binomial-variance?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-base-dists-negative-binomial-variance.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-base-dists-negative-binomial-variance/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-base-dists-negative-binomial-variance/tree/deno
[deno-readme]: https://github.com/stdlib-js/stats-base-dists-negative-binomial-variance/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/stats-base-dists-negative-binomial-variance/tree/umd
[umd-readme]: https://github.com/stdlib-js/stats-base-dists-negative-binomial-variance/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/stats-base-dists-negative-binomial-variance/tree/esm
[esm-readme]: https://github.com/stdlib-js/stats-base-dists-negative-binomial-variance/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/stats-base-dists-negative-binomial-variance/blob/main/branches.md

[negative-binomial-distribution]: https://en.wikipedia.org/wiki/Negative_binomial_distribution

[variance]: https://en.wikipedia.org/wiki/Variance

</section>

<!-- /.links -->

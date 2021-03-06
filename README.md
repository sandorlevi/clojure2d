# clojure2d

Clojure2D is a lightweight library supporting generative coding or glitching. It's based on Java2D directly. It's Clojure only, no ClojureScript version.

<img src="https://github.com/Clojure2D/clojure2d/blob/master/results/ex04/9973D635.jpg" alight="center" />

## Motivation

This project is the answer to personal needs to optimize my own workflow for generative or glitch creations. I've been producing a lot of Processing code and started to suffer from limitations of working in 'write sketch and run' mode. Too much copy&paste between sketches, zillions of folders, zillions of processed images. And one day I fell in love with FP. This code is the answer.

### What's wrong with Processing?

* not reusable code - you have to copy your common parts between sketches
* display and canvas coupling
* weak or no support for parallelism
* + more minor

### Why not use...

... quil, thi.ng, possibly other?

The main reason was that I wanted to learn Clojure making something from the scratch. Quil is still Processing. Thi.ng was to complex to me at the beginning (but I plan to investigate what can be usable).

### What's special in this library then?

In points:

* Almost decoupled display and canvas - you can have as many windows as you want, you can have as many canvases as you want. Display repaints selected canvas automaticaly in separate thread. This way you can operate on canvas in your way.
* Processing way is still possible (you can attach draw() function to your Display)
* Easy live coding possible (Emacs/Cider/REPL), 'notebook' way of making (like iPython)
* FastMath as main math library
* Main focus on higher level generative/glitch concepts (like sonification support, vector field functions, colorspace operations, things like pixelsorting, slitscan etc. See my Processing sketches, link below)

Check examples and results folders

### What's odd?

It's kind of personal library which supports my (probably not optimal, not convenient for others) way of creating.
There are still plenty of bugs and not idiomatic code. It's slower than Processing. Eats memory (Pixels code is generally immutable). Still not stable API and architecture.

## Installation

Add following line as a dependency to your `project.clj`

```clojure
[clojure2d "0.0.1-SNAPSHOT"]
```

## Usage

Since still no docs are available, check out prepared examples. There are available packages described below.

### clojure2d.core

This is main namespace with functions in three groups:

* image file oparations (load/save); jpg, png and bmp
* canvas operations (wrapper for Java2D BufferedImage and Graphics2D)
* display and event operations (JFrame wrapper)

### clojure2d.pixels

Definition of Pixels type as a representation of channel values of the image with operations on pixels.
Defines also:

* pixel filters (blur, erode, dilate, median, threshold, posterize, tint)
* blending (composing) function of two Pixels
* functions which operate on Pixels parallelly (filter-channels, blend-channels)

### clojure2d.color

* colorspace converters
* collection of blending basic functions (like add, subtract, divide, difference, etc.)

### clojure2d.math

* FastMath (jafama) bindings
* statistic functions
* random functions
* basic noise (flow-noise binding)

Additionally in following namespaces:

* clojure2d.math.complex - Complex type and operations (code taken from Apache Commons Math)
* clojure2d.math.vector - Vec2, Vec3 and Vec4 types and operations on vectors
* clojure2d.math.joise - Joise library bindings (basic, cell and fractal noise)

### clojure2d.extra

This is namespace for common generative/glitch specific libraries:

* filters - analog audio/video filters
* overlays - 3 overlays (noise, spots and rgb scanlines) to finish your images
* segmentation - segment Pixels into rectangles
* variariations - vector field functions / variations taken from Fractal Flame world

### clojure2d.utils

Couple of helper functions

## Examples

I've prepared several examples with results where you can check current state of the library and learn how it works. 

* ex01 - display window and process basic events (key and mouse)
* ex02 - simulate Processing draw() function
* ex03 - simple generative example
* ex04 - noise functions visualization
* ex05 - particle drawing
* ex06 - noise generative examples
* ex07 - more noise
* ex08 - folds code (http://folds2d.tumblr.com/)
* ex09 - curvature from noise (https://generateme.wordpress.com/2016/05/04/curvature-from-noise/)
* ex10 - second variant of curvature
* ex11 - pixel filters and image blending (composing)
* ex12 - 3 overlays
* ex13 - image segmentation example

## TODO

### High priority

* Marginalia docs + github.io page
* Cleaning, optimizations
* Parallel color operations on Pixels
* Color namespace cleaning
* Colorspace converters
* More in extra ns:
  - variations
  - code in extra namespace (moved from Processing)
  - analog filters (for sonification part)
* Canvas drawing functions (not filled shapes, PShape implementation)
* Session handling (saving results in session, logging actions)

### Low priority or ideas

* Cheat sheet
* More window events
* Deeper joise bindings
* Wavelets bindings

## Community

https://clojurians.slack.com/archives/clojure2d

### How to support

Yes! You can help with this project:

* Beginners:
  - create more variations
  - create colorspace converters
  - create pixel filters
  - create analog (audio) filters
* Advanced:
  - speed optimizations
  - idiomatic clojure fixes

Discuss about it with me on Slack.
Or just Pull Request.

## Projects

* Processing glitch/generative projects: https://github.com/tsulej/GenerateMe
* Visual log: http://generateme.tumblr.com/
* Folds project: http://folds2d.tumblr.com/
* Articles: https://generateme.wordpress.com/

## License

Copyright © 2016 GenerateMe
Distributed under the MIT Licence

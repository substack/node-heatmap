heatmap
=======

Heatmaps for node.js and the browser, groovy!

![groovy heatmap, man](http://substack.net/images/heatmap.png)

example
=======

blob.js
-------

````javascript
var heatmap = require('heatmap');

var heat = heatmap(500, 500, { radius : 30 });
for (var i = 0; i < 5000; i++) {
    var rho = Math.random() * 2 * Math.PI;
    var z = Math.pow(Math.random(), 2) * 200;
    
    var x = 250 + Math.cos(rho) * z;
    var y = 250 + Math.sin(rho) * z;
    
    heat.addPoint(x, y);
}
heat.draw();

var fs = require('fs');
fs.writeFileSync('blob.png', heat.canvas.toBuffer());
````

methods
=======

var heatmap = require('heatmap');

var heat = heatmap(...)
-----------------------

Create a new heatmap from an existing canvas element, a numeric width and
height, or an option object with canvas or width and height fields.

Optionally, you can set the `opts.radius` and `opts.threshold` to control the
rendering a little.

heat.addPoint(x, y, params)
---------------------------

Add a point to the heatmap with a `radius`.

`params` can have:

* radius, defaults to heat.radius || 20
* weight, defaults to 0.1

heat.scale(x, y)
----------------

Scale the canvas by the coefficients `x` and `y`.

If `y` is undefined, scale both x and y by the first parameter, `x`.

heat.draw()
-----------

Render all the points onto the canvas element.

heat.canvas
-----------

The HTML Canvas element.

Protip: with the [canvas module](https://github.com/LearnBoost/node-canvas) for
node you can `heat.canvas.buffer()` to get a Buffer with a PNG file all up in it.

install
=======

With [npm](http://npmjs.org), just do:

    npm install heatmap

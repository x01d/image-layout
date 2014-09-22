# image-layout

A collection of deterministic image layout algorithms written in pure javascript that work just as well on a server as in a browser.

```sh
$ npm install image-layout --save
```

### Sample Usage
```js
var layout = require('image-layout/layout/fixed-partition');
var elements = [
	{width: 400, height: 300},
	{width: 200, height: 100}
];

var result = layout(elements);
// container_width = result.width
// container_height = result.height
for (var i = 0, n = elements.length; i < n; i++) {
	// result.positions[i].x
	// result.positions[i].y
	// result.positions[i].width
	// result.positions[i].height
}
```

### Layouts

### fixed-columns

Simply balances photos into multiple columns.

```js
var layout = require('image-layout/layouts/fixed-columns');
var positions = layout(elements, {
    containerWidth: 800,
    columnCount: 3
});
```

### fixed-partition

Uses a partitioning scheme outlined by [Johannes Treitz](https://twitter.com/jtreitz) in ["The algorithm for a perfectly balanced photo gallery"](https://www.crispymtn.com/stories/the-algorithm-for-a-perfectly-balanced-photo-gallery). It's not the most-efficient option, but it leaves no ragged edges.

```js
var layout = require('image-layout/layouts/fixed-partition');
var positions = layout(elements, {
    containerWidth: 800,
    idealElementHeight: 300
});
```

## License

Copyright &copy; 2014 [Brian Reavis](https://github.com/brianreavis) & [Contributors](https://github.com/naturalatlas/image-layout/graphs/contributors)

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at: http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
# d3-random

以各种分布类型为基础生成随机数.

## Installing

NPM：`npm install d3-random`。也可以下载 [latest release](https://github.com/d3/d3-random/releases/latest). 还可以直接从 [d3js.org](https://d3js.org), 加载 [standalone library](https://d3js.org/d3-random.v1.min.js) 或作为 [D3 4.0](https://github.com/d3/d3) 的一部分引入. 支持 AMD, CommonJS 以及最基本的标签引入，通过标签引入会暴露  `d3` 全局变量:

```html
<script src="https://d3js.org/d3-random.v1.min.js"></script>
<script>

var random = d3.randomUniform(1, 10);

</script>
```

[Try d3-random in your browser.](https://runkit.com/npm/d3-random)

## API Reference

<a name="randomUniform" href="#randomUniform">#</a> d3.<b>randomUniform</b>([<i>min</i>, ][<i>max</i>]) [<>](https://github.com/d3/d3-random/blob/master/src/uniform.js "Source")

返回一个服从[uniform distribution(一般分布)](https://en.wikipedia.org/wiki/Uniform_distribution_\(continuous\))的随机数生成函数。随机数区间最小值和最大值由 *min* 和 *max* 参数决定。如果没有指定 *min* 则默认为 0，如果没有指定 *max* 则默认为 1。例如:

```js
d3.randomUniform(6)(); // 返回一个大于等于 0 且小于 6 的随机数.
d3.randomUniform(1, 5)(); // 返回一个大于等于 1 且小于 5 的随机数.
```

需要注意的是你也可以使用内置的 [Math.random](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/Math/random) 函数来直接生成服从一般分布的数值，比如设定成一个 0 到 99(包含) 之间的整数，可以使用 `Math.random() * 100 | 0`。

<a name="randomNormal" href="#randomNormal">#</a> d3.<b>randomNormal</b>([<i>mu</i>][, <i>sigma</i>]) [<>](https://github.com/d3/d3-random/blob/master/src/normal.js "Source")

返回一个服从 [normal (Gaussian) distribution(标准高斯分布)](https://en.wikipedia.org/wiki/Normal_distribution) 的随机数生成函数。期望值通过 *mu* 参数设置，标准差通过 *sigma* 参数设置。如果没有指定 *mu* 则默认为 0，如果没有指定 *sigma* 则默认为 1。

<a name="randomLogNormal" href="#randomLogNormal">#</a> d3.<b>randomLogNormal</b>([<i>mu</i>][, <i>sigma</i>]) [<>](https://github.com/d3/d3-random/blob/master/src/logNormal.js "Source")

返回一个服从 [log-normal distribution(对数分布)](https://en.wikipedia.org/wiki/Log-normal_distribution) 的随机数生成函数. 随机变量的自然对数期望值通过 *mu* 指定，标准差通过 *sigma* 指定。*mu* 默认为 0，*sigma* 默认为 1。

<a name="randomBates" href="#randomBates">#</a> d3.<b>randomBates</b>(<i>n</i>) [<>](https://github.com/d3/d3-random/blob/master/src/bates.js "Source")

返回一个服从 [Bates distribution(贝茨分布)](https://en.wikipedia.org/wiki/Bates_distribution) 的随机数生成函数，参数 *n* 表示独立变量个数。

<a name="randomIrwinHall" href="#randomIrwinHall">#</a> d3.<b>randomIrwinHall</b>(<i>n</i>) [<>](https://github.com/d3/d3-random/blob/master/src/irwinHall.js "Source")

返回一个具有 *n* 个独立变量的服从 [Irwin–Hall distribution(Irwin-Hall 分布)](https://en.wikipedia.org/wiki/Irwin–Hall_distribution) 的随机数生成函数。

<a name="randomExponential" href="#randomExponential">#</a> d3.<b>randomExponential</b>(<i>lambda</i>) [<>](https://github.com/d3/d3-random/blob/master/src/exponential.js "Source")

返回一个服从 [exponential distribution(指数分布)](https://en.wikipedia.org/wiki/Exponential_distribution) 的随机数生成函数。其中率参数为 *lambda* ；等价于给定时间区间内均值为 1 / *lambda* 的 [Poisson process(泊松过程)](https://en.wikipedia.org/wiki/Poisson_point_process) 时间发生次数。例如，exponential(1/40) 表示在平均每 40 个单位时间内发生一次事件之间的随机时间。 

<a name="random_source" href="#random_source">#</a> <i>random</i>.<b>source</b>(<i>source</i>)

返回用于生成随机数的相同类型的函数，但给定的随机数生成器源用作随机数的来源而不是Math.random。给定的随机数生成器必须实现与 Math.random 相同的接口并且输出值范围为 [0, 1). 当待选随机数生成器优于 Math.random 时这个方法会很有用。比如:

```js
var d3 = require("d3-random"),
    seedrandom = require("seedrandom"),
    random = d3.randomNormal.source(seedrandom("a22ebc7c488a3a47"))(0, 1);

random(); // 0.9744193494813501
```

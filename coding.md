# 1.命名规范（所有命名必须语义化！）
## 1.1 项目命名
全部采用小写方式， 以中划线分隔。

> 例：my-project-name

## 1.2 js文件命名
采用驼峰命名规则。

> 例：getUser.js

## 1.3 css,scss文件命名
采用驼峰命名规则。

> 例：loginPage.css

## 1.4 HTML文件命名
采用驼峰命名规则。

> 例：loginPage.html

# 2. HTML规范
## 2.1 语法
- 缩进使用soft tab（2个空格）
- 嵌套的节点应该缩进
- 在属性上，使用双引号，不要使用单引号
- 要忽略可选的关闭标签，(例如'</li>' 和 '</body>')
## 2.2 字符编码
通过声明一个明确的字符编码，让浏览器轻松、快速的确定适合网页内容的渲染方式，通常指定为'UTF-8'。

例如：

```
<meta charset="UTF-8">
```
 

## 2.3 减少标签数量
在编写HTML代码时，需要尽量避免多余的父节点；很多时候，需要通过迭代和重构来使HTML变得更少。

例如：
```
<!-- Not well -->
<span class="avatar">
    <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
 ```

## 2.4 实用优先原则
尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；i任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。

# 3. CSS规范 
项目中css可以使用 scss less 或者其他预编译，但整体需要遵循一下几点。

## 3.1 缩进
使用soft tab（2个空格）。

## 3.2 分号
每个属性声明末尾都要加分号。

## 3.3 换行
 

以下几种情况需要换行：

- '{' 后和 '}' 前
- 每个属性独占一行
- 多个规则的分隔符','后
例如：
```
/* not good */
.element
{color: red; background-color: black;}

/* good */
.element {
    color: red;
    background-color: black;
}

/* not good */
.element, .dialog {
    ...
}

/* good */
.element,
.dialog {
    ...
}
```
## 3.4 !important
不允许使用!important。

## 3.5 杂项
不允许有空的规则；

- 元素选择器用小写字母；

- 去掉数字中不必要的小数点和末尾的0；

- 属性值'0'后面不要加单位；

- 同个属性不同前缀的写法需要在垂直方向保持对齐，具体参照右边的写法；

- 无前缀的标准属性应该写在有前缀的属性后面；

- 不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；

- 不要在一个文件里出现两个相同的规则；

- 选择器不要超过4层（在scss中如果超过4层应该考虑用嵌套的方式来写）；



# 4. JS规范
首先，js规范必须遵循eslint规范，上线项目不允许出现eslint报错。其次，需要注意以下几点：

## 4.1 多行注释
最少三行, '*'后跟一个空格，具体参照右边的写法；

建议在以下情况下使用：

- 难于理解的代码段
- 可能存在错误的代码段
- 浏览器特殊的HACK代码
- 业务逻辑强相关的代码
例如：
```
/*
 * one space after '*'
 */
var x = 1;
```
## 4.2 文档注释
各类标签@param, @method等请参考usejsdoc和JSDoc Guide；

建议在以下情况下使用：

- 所有常量
- 所有函数
- 所有类
例如：
```
/**
 * @func
 * @desc 一个带参数的函数
 * @param {string} a - 参数a
 * @param {number} b=1 - 参数b默认值为1
 * @param {string} c=1 - 参数c有两种支持的取值</br>1—表示x</br>2—表示xx
 * @param {object} d - 参数d为一个对象
 * @param {string} d.e - 参数d的e属性
 * @param {string} d.f - 参数d的f属性
 * @param {object[]} g - 参数g为一个对象数组
 * @param {string} g.h - 参数g数组中一项的h属性
 * @param {string} g.i - 参数g数组中一项的i属性
 * @param {string} [j] - 参数j是一个可选参数
 */
function foo(a, b, c, d, g, j) {
    ...
}
```
## 4.3 变量命名
- 标准变量采用驼峰式命名（除了对象的属性外）
- 常量全大写，用下划线连接
- 构造函数，大写第一个字母
- jquery对象必须以'$'开头命名
- 'ID'在变量名中全大写
- 'URL'在变量名中全大写
例如：
```
var thisIsMyName;

var goodID;

var reportURL;

var MAX_COUNT = 10;

function Person(name) {
    this.name = name;
}

// not good
var body = $('body');

// good
var $body = $('body');
```
## 4.4 null
适用场景：

- 初始化一个将来可能被赋值为对象的变量
- 与已经初始化的变量做比较
- 作为一个参数为对象的函数的调用传参
- 作为一个返回对象的函数的返回值
不适用场景：

- 不要用null来判断函数调用时有无传参
- 不要与未初始化的变量做比较
4.5 undefined
永远不要直接使用undefined进行变量判断；
使用typeof和字符串'undefined'对变量进行判断。

例如
```
// not good
if (person === undefined) {
    ...
}

// good
if (typeof person === 'undefined') {
    ...
}
```
## 4.5 杂项
- 不要混用tab和space；
- 不要在一处使用多个tab或space；
- 换行符统一用'LF'；
- 对上下文this的引用命名范围：self > that > _this > me；
- 行尾不要有空白字符； 
- switch的falling through和no default的情况一定要有注释特别说明；
- 不允许三元运算符嵌套。
- 不允许有空的代码块。


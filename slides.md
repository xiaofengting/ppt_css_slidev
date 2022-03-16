---
theme: default
class: text-center
highlighter: shiki
download: true
title: CSS特性
---

# CSS 滤镜、混合模式

&nbsp;

CSS 特性

&nbsp;

                              ———— 贺晋飞



---
layout: quote
---

# 序言

&nbsp;

多年来，前端的创新都很多发生在JavaScript：
框架、模块、ECMAScript、打包构建、TypeScript。

事实上，同样奔三的 CSS 也一直再进化，获得了一些受欢迎的改进。  


现代浏览器的版本更新和迭代是非常迅速的。  
只要不需要兼容IE和Edge，可以利用强大的新特性写出很棒的效果。

今天 CSS 嵌套也有了进展，可能是编写CSS方式发生根本性改变的一年。



---
layout: quote
---

# 滤镜



---

| 滤镜                                  | 释义     |
| ------------------------------------- | -------- |
| filter: blur(5px)                     | 模糊     |
| filter: opacity(25%)                  | 透明度   |
| filter: brightness(1.4)               | 亮度     |
| filter: contrast(200%)                | 对比度   |
| filter: saturate(230%)                | 饱和度   |
| filter: hue-rotate(90deg)             | 色调变化 |
| filter: invert(75%)                   | 反相     |
| filter: grayscale(50%)                | 灰度     |
| filter: sepia(60%)                    | 褐色     |
| filter: drop-shadow(4px 4px 8px blue) | 投影     |


---

<img src="/filter-img.jpg">


---

# 模糊

<img class="filter-blur" src="/filter-img.jpg">


<style>
.filter-blur {
  width: 80%;
  animation: filter-blur 5s linear infinite alternate;
}
@keyframes filter-blur {
  0% {
    filter: blur(0)
  }
  100% {
    filter: blur(50px)
  }
}
</style>


---

# 透明度

<img class="filter-opacity" src="/filter-img.jpg">

<style>
.filter-opacity {
  width: 80%;
  animation: filter-opacity 5s linear infinite alternate;
}
@keyframes filter-opacity {
  0% {
    filter: opacity(0)
  }
  100% {
    filter: opacity(1)
  }
}
</style>





---

# 亮度

<img class="filter-brightness" src="/filter-img.jpg">

<style>
.filter-brightness {
  width: 80%;
  animation: filter-brightness 5s linear infinite alternate;
}
@keyframes filter-brightness {
  0% {
    filter: brightness(0.5)
  }
  100% {
    filter: brightness(1.5)
  }
}
</style>



---

# 对比度

<img class="filter-contrast" src="/filter-img.jpg">


<style>
.filter-contrast {
  width: 80%;
  animation: filter-contrast 5s linear infinite alternate;
}
@keyframes filter-contrast {
  0% {
    filter: contrast(50%)
  }
  100% {
    filter: contrast(150%)
  }
}
</style>



---

# 饱和度

<img class="filter-saturate" src="/filter-img.jpg">


<style>
.filter-saturate {
  width: 80%;
  animation: filter-saturate 5s linear infinite alternate;
}
@keyframes filter-saturate {
  0% {
    filter: saturate(50%)
  }
  100% {
    filter: saturate(200%)
  }
}
</style>




---

# 色调变化

<img class="filter-hue-rotate" src="/filter-img.jpg">


<style>
.filter-hue-rotate {
  width: 80%;
  animation: filter-hue-rotate 5s linear infinite alternate;
}
@keyframes filter-hue-rotate {
  0% {
    filter: hue-rotate(0)
  }
  100% {
    filter: hue-rotate(360deg)
  }
}
</style>




---

# hue-rotate 实现色彩流动

&nbsp;

发光效果使用 blur 滤镜。

<div class="loading-container" style="height: 250px;">
  <div class="loading-glow-ring"></div>
</div>

<style>
@keyframes loading-glow-ring {
  0% {
    transform: rotate(0deg);
    filter: hue-rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
    filter: hue-rotate(360deg);
  }
}
.loading-glow-ring {
  margin: 0 auto;
  position: relative;
  height: 150px;
  width: 150px;
  border-radius: 50%;
  background: linear-gradient(45deg, transparent, transparent 40%, #e5f403);
  animation: loading-glow-ring 2s linear infinite;
}
.loading-glow-ring::before {
  content: '';
  position: absolute;
  top: 6px;
  bottom: 6px;
  left: 6px;
  right: 6px;
  background: #fff;
  border-radius: 50%;
  z-index: 100;
}
.loading-glow-ring::after {
  content: '';
  position: absolute;
  top: 0px;
  bottom: 0px;
  left: 0px;
  right: 0px;
  background: linear-gradient(45deg, transparent, transparent 40%, #e5f403);
  border-radius: 50%;
  z-index: 1;
  filter: blur(30px);
}
html.dark .loading-glow-ring::before {
  background-color: rgba(18, 18, 18, 1);
}
</style>


---

# 反相

<img class="filter-invert" src="/filter-img.jpg">


<style>
.filter-invert {
  width: 80%;
  animation: filter-invert 5s linear infinite alternate;
}
@keyframes filter-invert {
  0% {
    filter: invert(0)
  }
  100% {
    filter: invert(1)
  }
}
</style>


---

# 灰度

<img class="filter-grayscale" src="/filter-img.jpg">


<style>
.filter-grayscale {
  width: 80%;
  animation: filter-grayscale 5s linear infinite alternate;
}
@keyframes filter-grayscale {
  0% {
    filter: grayscale(0%)
  }
  100% {
    filter: grayscale(100%)
  }
}
</style>


---

# 灰度用途

如清明节的时候，很多网站会换成灰色调。


---

# 褐色

<img class="filter-sepia" src="/filter-img.jpg">


<style>
.filter-sepia {
  width: 80%;
  animation: filter-sepia 5s linear infinite alternate;
}
@keyframes filter-sepia {
  0% {
    filter: sepia(0)
  }
  100% {
    filter: sepia(1)
  }
}
</style>


---

# drop-shadow
投影

`filter: drop-shadow(x偏移, y偏移, 模糊大小, 色值);`

另外两种阴影：  
1. box-shadow 盒阴影
2. text-shadow 文字阴影


---

# drop-shadow 透明

&nbsp;

可以给非透明部分（alpha通道）增加阴影效果。

<img class="drop-shadow-svg" src="/firefox-logo.svg">


<style>
.drop-shadow-svg {
  width: 200px;
  animation: drop-shadow-svg 5s linear infinite alternate;
}
@keyframes drop-shadow-svg {
  0% {
    filter: drop-shadow(0 0 10rem crimson);
  }
  20% {
    filter: drop-shadow(0 0 10rem #4444dd);
  }
  40% {
    filter: drop-shadow(10rem 0 10rem #4444dd);
  }
  60% {
    filter: drop-shadow(10rem 10rem 10rem rgb(160, 0, 210));
  }
  80% {
    filter: drop-shadow(0rem 10rem 10rem #4444dd);
  }
  100% {
    filter: drop-shadow(0rem 0rem 10rem crimson);
  }
}
</style>


---

# drop-shadow 实现三角倒影

<div class="drop-shadow">
  <i class="drop-shadow-cor"></i>
  filter: drop-shadow
</div>
<div class="box-shadow">
  <i class="drop-shadow-cor"></i>
  box-shadow
</div>

<style>
.drop-shadow-cor {
  position: absolute;
  left: -40px;
  width: 0;
  height: 0;
  overflow: hidden;
  border: 20px solid transparent;
  border-right-color: #ddd;
}
.drop-shadow {
  margin: 40px; padding: 50px;
  background-color: #ddd;
  position: relative;
  font-size: 24px;
  color: #000;
  filter: drop-shadow(5px 5px 10px black);
}
.box-shadow {
  margin: 40px; padding: 50px;
  background-color: #ddd;
  position: relative;
  font-size: 24px;
  color: #000;
  box-shadow: 5px 5px 10px black;
}
</style>


---

# 与 box-shadow 相比

drop-shadow不能叠加，没有 inset

<div class="loading-container loading-snake-container">
  <div class="loading-snake-border">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
  </div>
</div>

<style>
@keyframes loading-snake-border {
  0% {
    left: -100%;
  }
  25% {
    left: 0;
  }
  50%, 100% {
    left: 100%;
  }
}
@keyframes loading-snake-rotate {
  0% {
    transform: rotate(360deg);
  }
  100% {
    transform: rotate(0deg);
  }
}
.loading-snake-container {
  height: 350px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(45deg, #cfffd0, #3fff46);
}
.loading-snake-border {
  position: relative;
  width: 100px;
  height: 100px;
  animation: loading-snake-rotate 8s linear infinite;
  border: 10px dashed rgba(0, 0, 0, 0.2);
  box-shadow: 0 0 0 10px rgba(0, 0, 0, .5),
              inset 0 0 0 10px rgba(0, 0, 0, .4);
}
.loading-snake-border span {
  position: absolute;
  display: block;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.loading-snake-border span::before {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  border-top: 10px solid #fff;
  left: -100%;
  animation: loading-snake-border 2s linear infinite;
}
.loading-snake-border span:nth-child(1) {
  transform: rotate(0deg);
}
.loading-snake-border span:nth-child(2) {
  transform: rotate(90deg);
}
.loading-snake-border span:nth-child(3) {
  transform: rotate(180deg);
}
.loading-snake-border span:nth-child(4) {
  transform: rotate(270deg);
}
.loading-snake-border span:nth-child(1)::before {
  animation-delay: 0s;
}
.loading-snake-border span:nth-child(2)::before {
  animation-delay: 0.5s;
}
.loading-snake-border span:nth-child(3)::before {
  animation-delay: 1s;
}
.loading-snake-border span:nth-child(4)::before {
  animation-delay: 1.5s;
}
</style>


---

# drop-shadow 与 box-shadow 结合使用


<!-- 文字配环loading -->
<div class="loading-container-ring">
  <div class="loading-text-in-ring-text">loading</div>
  <div class="loading-text-in-ring"></div>
</div>

<style>
@keyframes rotate360 {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.loading-container-ring {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 320px;
  width: 320px;
  overflow: hidden;
}
.loading-text-in-ring {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  box-shadow: 0 4px 0 #262626;
  filter: drop-shadow(0 0px 10px red);
  background: transparent;
  animation: rotate360 1s linear infinite;
}
.loading-text-in-ring-text {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  color: #262626;
  position: absolute;
  top: 60px;
  left: 60px;
  text-align: center;
  font-size: 36px;
  background-color: transparent;
  line-height: 200px;
  text-transform: uppercase;
}
html.dark .loading-text-in-ring {
  box-shadow: 0 4px 0 #fff;
  filter: drop-shadow(0 0px 10px red);
}
html.dark .loading-text-in-ring-text {
  color: #fff;
  box-shadow: 0 0 5px rgba(255, 255, 255, .2);
}
</style>


---

# backdrop-filter

为元素的背后区域添加滤镜。

值和 filter 取值相同。

`backdrop-filter: blur(5px)`

目前只支持 webkit 浏览器

[can i use](https://caniuse.com/?search=backdrop-filter)



---

# backdrop-filter 实现玻璃效果

<div>
  <div class="loading-glass-circle">
    <span></span>
    <span></span>
  </div>
</div>

<style>
@keyframes loading-glass-circle-one {
  0%, 100% {
    transform: translateX(-80px);
  }
  50% {
    transform: translateX(80px);
  }
}
.loading-glass-circle {
  position: relative;
  width: 120px;
  height: 120px;
  margin: 50px 100px 100px;
}
.loading-glass-circle span {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background:#5989ff;
  border-radius: 50%;
  animation: loading-glass-circle-one ease-in-out 2s infinite;
}
.loading-glass-circle span:nth-child(2) {
  background-color: rgba(56, 109, 241, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  animation-delay: -1s;
}
.loading-glass-circle span::before {
  content: '';
  position: absolute;
  bottom: -80px;
  left: -20%;
  width: 140%;
  height: 40px;
  border-radius: 50%;
  background: radial-gradient(rgba(0,0,0,0.1),transparent,transparent);
}
</style>


---

# backdrop-filter 实现loading

<div style="margin-bottom: 60px;">
  <div class="loading-glass-circle-2">
    <span></span>
    <span></span>
  </div>
</div>

<style>
@keyframes rotate360 {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.loading-glass-circle-2 {
  position: relative;
  width: 180px;
  height: 180px;
}
.loading-glass-circle-2 span:nth-child(1) {
  position: absolute;
  top: 10px;
  left: 10px;
  right: 10px;
  bottom: 10px;
  background-color: rgba(233, 30, 99, 0.05);
  border-radius: 50%;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  z-index: 2;
}
.loading-glass-circle-2 span:nth-child(2) {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: block;
  border-radius: 50%;
  z-index: 1;
  overflow: hidden;
  animation: rotate360 1s linear infinite;
}
.loading-glass-circle-2 span:nth-child(2)::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 100%;
  height: 100%;
  background: #ff6198;
}
.loading-glass-circle-2 span:nth-child(1)::before {
  content: '';
  position: absolute;
  bottom: -80px;
  left: -20%;
  width: 140%;
  height: 40px;
  border-radius: 50%;
  background: radial-gradient(rgba(0,0,0,0.1),transparent,transparent);
}
</style>


---

# `<blend-mode>`

混合模式


---

# conic-gradient()

圆锥渐变






---

# attr()

获取选择到的元素的某一HTML属性值

实验中的功能。  
目前仅支持作为字符串，用于伪元素的 content 属性。

[can i use](https://caniuse.com/css-gencontent)

可以作为一种 tooltip 的实现。

<p data-title="这里是很长的一段提示。这里是很长的一段提示。这里是很长的一段提示。这里是很长的一段提示" class="title-after">悬浮查看提示</p>

<style scoped>
.title-after {
  position: relative;
}
.title-after:hover::after {
  content: attr(data-title);
  font-size: 14px;
  position: absolute;
  z-index: 1;
  top: 24px;
  left: 0;
  max-width: 160px;
  padding: 12px;
  border: 1px #aaa solid;
  border-radius: 10px;
  background-color: #ffc;
}
html.dark .title-after:hover::after {
  color: #000;
}
</style>


---


<section class="menu-bg-container">
  <ul>
    <li class="menu-bg-item">
      <a href="#" data-text="home">home</a>
    </li>
    <li class="menu-bg-item">
      <a href="#" data-text="about">about</a>
    </li>
    <li class="menu-bg-item">
      <a href="#" data-text="service">service</a>
    </li>
    <li class="menu-bg-item">
      <a href="#" data-text="team">team</a>
    </li>
    <li class="menu-bg-item">
      <a href="#" data-text="contact">contact</a>
    </li>
  </ul>
</section>

<style scoped>
.menu-bg-container {
  position: relative;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1;
}
.menu-bg-container ul {
  display: flex;
  flex-direction: column;
  margin: 0;
  line-height: 1.5 !important;
}
.menu-bg-item {
  list-style: none;
}
.menu-bg-item a {
  display: block;
  text-decoration: none;
  text-align: center;
  font-size: 30px;
  font-weight: 700;
  color: #000;
  text-transform: uppercase;
  border: none;
}
.menu-bg-item a::before {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  overflow: hidden;
  font-size: 3em;
  color: #2196f3;
  opacity: 0;
  line-height: 400px;
  transition: 0.5s;
}
.menu-bg-item:hover a::before {
  opacity: 1;
}
html.dark .menu-bg-item a {
  color: #fff;
}
</style>


---

# -webkit-text-stroke

文字填充的颜色

兼容性好，但是非标准属性。

[can i use](https://caniuse.com/?search=-webkit-text-stroke)

&nbsp;

<ul class="colorful-menu">
  <li style="--clr: #00ade1">
    <a href="#" data-text="&nbsp;&nbsp;HOME&nbsp;">&nbsp;&nbsp;HOME&nbsp;</a>
  </li>
  <li style="--clr: #ffdd1c">
    <a href="#" data-text="&nbsp;&nbsp;ABOUT&nbsp;">&nbsp;&nbsp;ABOUT&nbsp;</a>
  </li>
  <li style="--clr: #00dc82">
    <a href="#" data-text="&nbsp;&nbsp;SERVICES&nbsp;">&nbsp;&nbsp;SERVICES&nbsp;</a>
  </li>
  <li style="--clr: #dc00d4">
    <a href="#" data-text="&nbsp;&nbsp;CONTACT&nbsp;">&nbsp;&nbsp;CONTACT&nbsp;</a>
  </li>
</ul>

<style scoped>
.colorful-menu li {
  position: relative;
  list-style: none;
}
.colorful-menu li a {
  position: relative;
  font-size: 30px;
  text-decoration: none;
  overflow-wrap: normal;
  color: transparent;
  -webkit-text-stroke: 1px rgba(0, 0, 0, 0.5);
}
.colorful-menu li a::before {
  content: attr(data-text);
  position: absolute;
  color: var(--clr);
  z-index: 1;
  width: 0;
  overflow: hidden;
  transition: 1s;
  border-right: 8px solid var(--clr);
  -webkit-text-stroke: 1px var(--clr);
}
.colorful-menu li a:hover {
  text-decoration: none;
}
.colorful-menu li a:hover::before {
  width: 100%;
}
html.dark .colorful-menu li a {
  -webkit-text-stroke: 1px rgba(255, 255, 255, 0.5);
}
</style>


---

# -webkit-box-reflect

创建倒影

非标准属性，-webkit- 内核的浏览器支持。

[can i use](https://caniuse.com/?search=-webkit-box-reflect)

[巧用倒影](https://github.com/chokcoco/iCSS/issues/100)

[创造艺术图案](https://yuanchuan.dev/2019/05/15/window-lattice-and-css.html)

---

<section class="reflect-btn-container" style="--color: #0ebeff;">
  <div class="reflect-btn">Neon</div>
  <div class="reflect-btn reflect-btn1">Neon</div>
  <div class="reflect-btn reflect-btn2">Neon</div>
  <div class="reflect-btn reflect-btn3">Neon</div>
</section>

<style>
.reflect-btn-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 400px;
  background: #000;
}
@keyframes rotate {
  100% {
    transform: translate(-50%, -50%) rotate(1turn);
  }
}
.reflect-btn {
  position: relative;
  z-index: 0;
  width: 160px;
  height: 80px;
  line-height: 80px;
  color: var(--color);
  font-size: 24px;
  border-radius: 10px;
  text-align: center;
  margin: auto;
  overflow: hidden;
  cursor: pointer;
  transition: .3s;
  -webkit-box-reflect: below 10px linear-gradient(transparent, rgba(0, 0, 0, .4));

  &:hover {
    color: #fff;
    box-shadow: 0 0 5px var(--color),
      0 0 25px var(--color);
    
    &::after,
    &::before {
      transition: .3s;
      background: var(--color);
    }
  }
  
  &::before {
    content: '';
    position: absolute;
    z-index: -2;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 150%;
    height: 300%;
    background-color: #000;
    background-repeat: no-repeat;
    background-size: 50% 50%;
    background-position: 0 0;
    background-image: conic-gradient(var(--color), var(--color));
    animation: rotate 2s linear infinite;
  }
  
  &::after {
    content: '';
    position: absolute;
    z-index: -1;
    left: 2px;
    top: 2px;
    width: calc(100% - 4px);
    height: calc(100% - 4px);
    background: #000;
    border-radius: 10px;
  }
}
.reflect-btn1 {
  filter: hue-rotate(180deg);
}

.reflect-btn2 {
  filter: hue-rotate(270deg);
}

.reflect-btn3 {
  filter: hue-rotate(90deg);
}
</style>


---


<div class="loading-climb-outer-container">
  <div class="loading-climb-container">
    <div class="loading-climb-box">
      <div class="loading-climb-cube"></div>
    </div>
  </div>
</div>

<style>
@keyframes loading-cube-climb-boxmove {
  0% {
    transform: translateX(0px);
  }
  100% {
    transform: translateX(-150px);
  }
}
@keyframes loading-cube-climb-cubemove {
  0% {
    transform: rotate(0deg);
  }
  60% {
    transform: rotate(90deg);
  }
  65% {
    transform: rotate(85deg);
  }
  70% {
    transform: rotate(90deg);
  }
  75% {
    transform: rotate(87.5deg);
  }
  80%, 100% {
    transform: rotate(90deg);
  }
}
.loading-climb-outer-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  background-color: #22272e;
  overflow: hidden;
}
.loading-climb-container {
  position: relative;
  width: 100%;
  transform: rotate(-35deg);
}
.loading-climb-container .loading-climb-box { 
  position: relative;
  left: -150px;
  display: flex;
  justify-content: center;
  align-items: center;
  width: calc(100% + 300px);
  -webkit-box-reflect: below 1px linear-gradient(transparent, #0004);
  animation: loading-cube-climb-boxmove 1.5s ease-in-out infinite;
}
.loading-climb-box .loading-climb-cube {
  position: relative;
  width: 150px;
  height: 150px;
  background-color: #03e9f4;
  box-shadow: 0 0 5px rgba(3, 233, 244, 1),
              0 0 25px rgba(3, 233, 244, 1),
              0 0 50px rgba(3, 233, 244, 1),
              0 0 100px rgba(3, 233, 244, 1),
              0 0 200px rgba(3, 233, 244, 1);
  transform-origin: bottom right;
  animation: loading-cube-climb-cubemove 1.5s ease-in-out infinite;
}
</style>





---
layout: end
---


---

# aspect-ratio

纵横比

例如：  

```
aspect-ratio: 16 / 9;
```


---
layout: quote
---

# 技术与工具


---

# 预/后处理

&nbsp;

1. [PostCSS](https://www.postcss.com.cn/)：后处理器。

类似babel对js。  
使用下一代css语法；补全浏览器前缀；代码压缩。

2. [Sass](https://www.sass.hk/)：预处理器。

CSS的扩展语言。  
变量；嵌套；运算；函数；混合。


---

# CSS 框架

&nbsp;

1. [Tailwind CSS](https://www.tailwindcss.cn)

utility 。无需写一行 CSS  
以实用为先，提供了高度可组合的功能类。


2. [Pure.css](https://www.purecss.cn/)

轻量级、响应式纯css模块。

3. [Ant Design](https://ant.design/index-cn)

UI 组件库。


---

# CSS in JS

&nbsp;

1. [CSS Modules](https://www.ruanyifeng.com/blog/2016/06/css_modules.html)

模块化CSS，可用来替代scoped CSS。  
Vite 原生支持。

2. [styled-components](https://github.com/styled-components/styled-components)

React 样式方案中最受关注的一种。

3. [Stitches](https://stitches.dev/)

可能是 CSS-in-JS 的最佳实现。


---

# 新技术

&nbsp;

1. [vanilla-extract](https://vanilla-extract.style/documentation)

适用于 TypeScript 。CSS Modules-in-TypeScript

2. [Windi CSS](https://windicss.org/)

以 Tailwindcss 为灵感制作，更快，兼容性更好。

---

# CSS 方法论

&nbsp;

1. utility-first（Atomic CSS）

实用主义，用海量的实用工具类。Tailwind CSS、Windi CSS。

2. BEM

Block, element, modifier。块层、元素层、修饰符层。  
命名使用 `__` 和 `--`，例 container__paragraph--bold

3. ITCSS

将CSS代码分成七层。

<!-- OOCSS：面向对象的CSS -->

<!-- SMACSS：分为5类 -->

4. [CUBE](https://cube.fyi)


---

# 规范化

&nbsp;

1. Stylelint：CSS 代码检查规范。
2. Prettier：通用的代码格式化工具。
3. PurgeCSS ：去除不使用的CSS代码。
4. PurifyCSS：去除无用的CSS代码。
5. cssnano：更好的压缩CSS
6. Autoprefixer：加浏览器前缀。
7. CSSComb：CSS排序。


---
layout: quote
---

# 资源


---

# CSS 艺术家

&nbsp;

[css-doodle](https://github.com/css-doodle/css-doodle)

[ppt](https://yuanchuan.dev/talk/generative-art-with-css/)


---

# 有趣的动画项目

&nbsp;

1. [CSS项目](https://github.com/ManrajGrover/SingleDivProject)

单个 div 做动画。

2. [ChokCoco](https://github.com/chokcoco/iCSS)

动画为主的中文博客。

3. [CSS trick](https://lhammer.cn/You-need-to-know-css/#/zh-cn/)

Web开发者需要知道的CSS Tricks

4. [张鑫旭博客](https://www.zhangxinxu.com/)


---

# 年度报告

&nbsp;

1. [JavaScript明星项目](https://risingstars.js.org/2021/zh)

从 2015年 开始每年一次的 GitHub 前端项目总结。

2. [CSS年度使用报告](https://2021.stateofcss.com/zh-Hans/)

从 2019年 开始每年一次的调查问卷。  
和 [JS年度使用报告](https://2021.stateofjs.com/zh-Hans/) 同团队作品。




---

# 其他网站

&nbsp;

1. [玩转CSS动画](https://keyframes.app/animate/)

2. [缓动函数速查](https://easings.net/cn)


---
layout: quote
---

# 总结


木匠需要每年去学习一种新的，更好的方式去锯木头吗？  
画家会因为自己仍然在使用油漆作画而感到自己落伍了吗？  
还是说只有我们前端开发者才能体验到前端领域的不断变化？


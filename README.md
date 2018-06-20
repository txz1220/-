# 一个模仿天猫网页的项目

主要涉及到前端方面，后端暂无。

主要目的：拿来练手用的

>本项目主要是联系使用，所以css js 都放在html页面上了。


### 知识点学习：

#### 1、html

要有个布局框架
![](https://ws1.sinaimg.cn/large/006c6oKBgy1fshgpbe9p0j30qp0c6mz4.jpg)

#### 2、css

要有层次写，首先写最上层的body 、div  依次写样式。  最好有继承关系，没有继承关系的再单写。

#### 3、js 交互

逻辑层次要强


 

#### 1、产品页-产品图片

##### html

设置clss id 值   命名规范化。

##### css

1、首先设置body的字体样式
2、顶层div的magin  最好居中显示 auto
3、子元素最基本元素的设置长宽高等   float 让其水平显示
4、overflow: hidden;
隐藏溢出部分。 结合图片div的float:left,就可以做到基本信息div和图片div水平摆放，并且基本信息div自动占用剩下所有的宽度

5、border-bottom-style: dotted; 设置虚线

6、block  和 inline-block 的区别

**display: inline-block;
显示为内联，既可以设置大小，又能够不换行
display: block;
显示为块级元素，自动换行**


#### 2、产品页-产品详情页

1、整体居中  margin: 40px auto;

2、选择器  a.selected  被选中时呈现的样式



3、position: relative;
相对定位，为的是下一步使用:before新增加的元素做绝对定位。 因为绝对定位是基于定位了的父元素


```css
a.selected:before{
    content:"";
内容为空
display: block;
以块状显示，便于修改宽度
    position: absolute;
绝对定位，其父元素超链是相当定位的，所以这绝对定位就会基于父元素
top: -1px;
向上移动一个像素
margin-left: -1px;
左外边距: -1px，向左边移动一个像素，导致和左边的边框重合
}
```

美人尖的制作方法：

```css
a.selected:after{
content: "";
内容为空
display: block;
以块状显示，便于修改宽度
border-color: #b00000 transparent transparent;
美人尖的原理是只有上边框，其他边框是透明色，#b00000 transparent transparent; 这种写法既表示只有上边框有颜色，其他都是透明色
border-style: solid;
边框实线
border-width: 5px;
边框宽度
width: 0;
宽度: 0
height: 0;
高度: 0
position: absolute;
绝对定位
top: -1px;
向上移动1个像素
left: 50%;
居中
margin-left: -5px;
向左边移动-5px
}
```

#### 2、产品页-交互


**具体详见源代码注释**



a、显示缩略图效果

所有的事件放在$(function(){}  里面  

选择器-----添加事件监听-----获取需要的节点、属性等-------如果需要判断就判断----------改变需要改变


b、修改价格


获取输入框的值  num=$(".shuxing").val()

把字符转换数字  num= parseInt(num)

进行判断  判断是不是数字类型  if(isNaN(num)){ num=1 }   判断是不是小于等于零， if(num<=0){ num = 1;}

判断是不是大于库存    if(num>stock){ num = stock;}



添加点击事件：  选择器（增加按钮）.click( function() {


})

先初始化输入框数量  var num= $(".productNumberSetting").val();

num++ //没点击一次增加数量1

判断： 如果大于库存  if(num>stock)
        num = stock;

    $(".productNumberSetting").val(num);





选择器（减少按钮）.click( function() {


})

先初始化输入框数量  var num= $(".productNumberSetting").val();

--num //没点击一次减少数量1


判断是不是小于等于零了：if(num<=0){num=1;}  获取当前值  $(".productNumberSetting").val(num);
            

       












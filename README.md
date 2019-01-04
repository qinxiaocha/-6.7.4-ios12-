# -6.7.4-ios12-
微信6.7.4 ios12软键盘顶起页面后隐藏不回弹解决方案
## bug复现
情况说明：
在2018.11.30号一个明媚的下午，测试跟我反馈说ios出现了bug，怀着一定是你姿势不对的心里我自己悄悄的点了一下，我去，居然也出现了，可是昨天还没有啊，开始排查代码，发现没有任何问题，于是用其他版本的ios和微信测试，发现只有在ios12+，微信6.7.4版本才有，然后又看了一下微信6.7.4也是刚更新，为了在验证一下是不是自己的代码问题，于是打开了之前写的项目和自己写了一个静态的html都复现了该bug，所以就很开心的定位到了问题(此时脸上笑嘻嘻)。


   temporaryRepair(){
    var currentPosition,timer;
    var speed=1;//页面滚动距离
    timer=setInterval(function(){
        currentPosition=document.documentElement.scrollTop || document.body.scrollTop;
        currentPosition-=speed; 
        window.scrollTo(0,currentPosition);//页面向上滚动
        currentPosition+=speed; //speed变量
        window.scrollTo(0,currentPosition);//页面向下滚动
        clearInterval(timer);
    },1);
}
var wechatInfo = navigator.userAgent.match(/MicroMessenger\/([\d\.]+)/i);
var wechatVersion = wechatInfo[1] 
var u = navigator.userAgent.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/);
if(wechatVersion=='6.7.4'&&!!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/)){
...代码逻辑
}
--------------------- 

原文：https://blog.csdn.net/qq_23370345/article/details/84757505 

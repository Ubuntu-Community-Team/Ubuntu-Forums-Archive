---
title: "Run javascript in child div without running javascript on parent div"
date: 2013-05-06
forum: Programming Talk
---

### Post by mandza on 2013-05-06
Hi,
i want to make few javascript function that run separately from each other
this is code i want to make working

HTML CODE:
[FONT=monospace]<a href="javascript:void(0);" onclick="resimgoster(1)" >[/FONT][COLOR=#000000][FONT=monospace]Resimler deneme[/FONT][/COLOR][FONT=monospace]</a>[/FONT]
<div class="zhresimler" id="zhresimler" onclick="resimgizle()">
<div style="width:100px; height:100px; overflow:auto; border:solid 1px #ffffff; z-index:999;" onclick="alert('Problem')">Deneme</div>
</div>

CSS CODE:

div.zhresimler {width:0px; height:0px; top:0px; left:0px; overflow:hidden;}div.zhresimler_on {position:fixed; width:100%; height:100%; top:0px; left:0px; background-color:rgba(0,0,0, 0.7);}JS CODE:function resimgoster(resimid) {
var resimid;
document.getElementById('zhresimler').setAttribute("class", "zhresimler_on");
}


function resimgizle() {
document.getElementById('zhresimler').setAttribute("class", "zhresimler");
}


When i click on resimgoster(1) it open div that i want. and i have one more div inside it. when i click on inside (child div) i want to run function for example alert, but when i click elsewhere i want to run resimgizle()

Thank you for your help

---

### Post by mandza on 2013-05-06
i solved my problem with

setTimeout(\"resimgoster(1)\", 5);

but is there any other solutions???
with setTimeout i run same function after 5ms.

---

### Post by epicoder on 2013-05-07
Much more context is needed if you want a helpful response. I have no idea what you are trying to do here. There is, however, one hint I can give you- Don't pass a string to setTimeout. You are essentially calling eval, which as we all know, is [evil]("http://jslint.com/lint.html#evil"). Use this code instead:
```
setTimeout(function () { resimgoster(1); }, 5);
```
This passes a function instead of a string to compile and thus avoids the implicit eval completely.

Also, put code tags around your code like I did above. It makes your code 100% more readable and forumites everywhere will be grateful.
[noparse]```
Your code here...
```[/noparse]

---


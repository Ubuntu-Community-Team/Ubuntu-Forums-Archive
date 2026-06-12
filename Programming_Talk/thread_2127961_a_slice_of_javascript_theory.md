---
title: "a slice of javascript theory?"
date: 2013-03-21
forum: Programming Talk
---

### Post by maclenin on 2013-03-21
Given the array:
```
var a=[4,5,6,7,8,9];
```
Why does...

instance A: ```
**x=4;**
document.write(x);
if (a.indexOf(x)!=-1) {document.write("yep!");}
else {document.write("nope!");} 
```...yield yep!

instance B: ```
**x=a[0];**
document.write(x);
if (a.indexOf(x)!=-1) {document.write("yep!");}
else {document.write("nope!");} 
```...yield yep!, ***but***...

instance C: ```
**x=a.slice(0,1);**
document.write(x);
if (a.indexOf(x)!=-1) {document.write("yep!");}
else {document.write("nope!");} 
```...yield nope!

**When**, for all instances (A,B,C)...
```
document.write(x);
```...yields 4

Thanks for any guidance!

---

### Post by Zugzwang on 2013-03-21
Dear OP, you've got to admit that your question looks a bit like homework. Thus, I shall not give more than a hint: "types". There are many sources reading more about types in JavaScript.

---

### Post by QIII on 2013-03-22
maclenin's post is not a homework question and the thread has been restored.

Cheers!

---

### Post by iMac71 on 2013-03-23
```
var a=[4,5,6,7,8,9];
xB=a[0]; // x of instance B
xC=a.slice(0,1); // x of instance C
document.write(xB + "<br>");
document.write(a.indexOf(xB) + "<br>");
document.write(xC + "<br>");
document.write(a.indexOf(xC) + "<br>");
document.write((xB===xC) + "<br>");
```the result of test in last line shows that xB and xC aren't of the same type: xB is a number, while xC is an array (see here: [http://www.w3schools.com/jsref/jsref_slice_array.asp](http://www.w3schools.com/jsref/jsref_slice_array.asp)).

---

### Post by maclenin on 2013-03-23
**QIII!**

Thanks, again.

**iMac71!**

Thanks for your test scenario. I hear you.

With your lessons in mind (and via [jsbin's]("http://jsbin.com/#javascript,html,live") lab)...

```
var a=[4,5,6,7,8,9];
var b=[0,4,8,12,16,20];

xC=a.slice(0,1);
xD=a.slice(0,1);

y=b.indexOf(xC);
y1=b.indexOf(xC[0]);

z=b[xC];
z1=b[xC[0]];

document.write("xC=array <i>"+typeof(xC)+"</i> <b>xC</b> contains <i>"+typeof(xC[0])+"</i>(s) <b>"+xC+"</b> from array <i>"+typeof(a)+"</i> <b>a</b><br>");
document.write("xD=array <i>"+typeof(xD)+"</i> <b>xD</b> contains <i>"+typeof(xD[0])+"</i>(s) <b>"+xD+"</b> from array <i>"+typeof(a)+"</i> <b>a</b><br>");
document.write("<br>");
document.write("y=the indexOf array <i>"+typeof(xC)+"</i> <b>xC</b> in array <i>"+typeof(b)+"</i> <b>b</b> is <b>"+y+"</b><br>");
document.write("y1=the indexOf <i>"+typeof(xC[0])+"</i> <b>"+xC+"</b> in array <i>"+typeof(b)+"</i> <b>b</b> is <b>"+y1+"</b><br>");
document.write("<br>");
document.write("z=the <i>"+typeof(z)+"</i> <b>"+z+"</b> is in position "+xC+"  in array <i>"+typeof(b)+"</i> <b>b</b><br>");
document.write("z1=the <i>"+typeof(z1)+"</i> <b>"+z1+"</b> is in position "+xC[0]+"  in array <i>"+typeof(b)+"</i> <b>b</b><br>");
document.write("<br>");
document.write("Should the result of \"(xC===xD)\" be <b>"+(xC===xD)+"</b>?<br>");
document.write("<br>");
document.write(xC+"<br>");
document.write(xD+"<br>");
```

...these questions emerge:

1. for y, why is xC treated as an object, whereas for z, xC seems to resolve to the number 4?

2. for y1 (and z1), it seems treating xC as an object with [reference] to a specific element allows xC to be evaluated by indexOf.

3. xC===xD is still false, should this be so? Perhaps, yes? See the bottom of [this page]("https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Operators/Comparison_Operators#Using_the_Equality_Operators").

4. xC and xD BOTH resolve to the number (?) 4 via document.write().

Thanks, again, for your help!

---

### Post by iMac71 on 2013-03-23
> **maclenin said:**
> 1. for y, why is xC treated as an object, whereas for z, xC seems to resolve to the number 4?because for z you use the square brackets instead of indexOf(), hence [xC] becomes a kind of reference instead of a single element array
> **maclenin said:**
> 2. for y1 (and z1), it seems treating xC as an object with [reference] to a specific element allows xC to be evaluated by indexOf.xC[0] is the first element of xC, i.e. 4, which is a number: hence xC[0] can be used for finding its value into array b[] with indexOf
> **maclenin said:**
> 3. xC===xD is still false, should this be so? Perhaps, yes? See the bottom of [this page]("https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Operators/Comparison_Operators#Using_the_Equality_Operators").Perhaps the reason could be that two variables of identical type and identical content occupy different memory places, hence the '===' operator gives false as the result of comparison between them.
> **maclenin said:**
> 4. xC and xD BOTH resolve to the number (?) 4 via document.write().

Thanks, again, for your help!xC and xD are single element arrays, while xC[0] and xD[0] are numbers

---


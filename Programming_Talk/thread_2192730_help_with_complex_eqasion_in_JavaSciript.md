---
title: "help with complex eqasion in JavaSciript"
date: 2013-12-09
forum: Programming Talk
---

### Post by johnnycatt on 2013-12-09
I didn't know where to take this, but the best coders and hackers are using Linux (and you guys have solved a few linux problems for me in the past) so I figured I'd lay it on you:

I have been trying to learn JavaScript (yes, Noob - only about 25 hours of study on it).  I have always had a pretty good grasp of HTML, but I am really having a hard time getting them to work together to create a "fuction" (and that may be the wrong "operator") where I can solve an equasion I use at work.

Is there anyone who wants to give it a shot, it REALLY does not look that hard.  I can get the "equasion" to work if I use constants, but when I try to use variables, all the sudden the Function forgets how to function!!

This has really infuriated me and I just can NOT quite get it to work.  I can get JavaScript to do "simple" equasions, but once I start trying to Math.sqrt() or Math.pow(x,y) it all goes haywire.  As a matter of fact, I have tried to get it to solve for just "a+b" by making var d = (a+b); but when I try "innerHLTM = parceFloat(d);"  It cannot even add the two numbers... SO I KNOW SOMETHING I'M DOING IS WRONG!!

The Equasion I am trying to solve for is:

L = 2c + 1.57 (a + b) + (((a - b)^2)/4c)  [The last part is ((a-b)squared) devided by (4 times c)]

I need to get my "a" and "b" variables from drop-down boxes so that only certain "sizes" can be used.  "c" is just an inputed number.

Any help would be appreciated!!!!

I have the following written:

**********************************************************************************************************************************************************
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>total size</title>
</head>
<body>

<center><bold><h1>Total Size<h1></bold></center>

<P> item A:

  <select id="vara">
<option value="3.4">3.75</option>
<option value="3.6">3.95</option>
<option value="3.8">4.15</option>
<option value="4.0">4.35</option>
</select>
</p>

<P>item B:
   <select id="varb">
<option value="3.4">3.75</option>
<option value="3.6">3.95</option>
<option value="3.8">4.15</option>
<option value="4.0">4.35</option>
</select></P>
<p>distance: 
<input id="varc" type="text" />
</p>
<button onclick="output()">Get total size</button>
</p>

Total size: <p id="result"> </p>
<script type="text/javascript" language="javascript" charset="utf-8">

function output(){
var a = document.getElementById('vara').value;
var b = document.getElementById('varb').value;
var c = document.getElementById('varc').value;
var d = (a+b);
var e = (a-b);
var f = ((c)*2);
var g = ((d)*1.57);
var h = Math.pow((e),2);
var i = ((h)/(f*2));
document.getElementById('result').innerHTML = parseFloat(f) + parseFloat(g) + parseFloat(i);
}

 
</script>
</center>
</body>
</html>

---

### Post by Bucky Ball on 2013-12-09
*Thread moved to **Programming Talk**.*

***The Cafe*** is not a support area.

---

### Post by johnnycatt on 2013-12-09
I realize this, But I was hoping for some direction or just an answer

Thanks for putting where it should have been!

---

### Post by Bucky Ball on 2013-12-09
> **johnnycatt said:**
> ... I was hoping for some direction or just an answer


All good. The direction was here as you wouldn't have gotten an answer there (stricly water-cooler chat). You have a much better chance here if you're looking for 'coders and hackers'. ;)

---

### Post by koenn on 2013-12-09
smells a bit like a home work question, but anyway.
this seems to work, but no guaranrues, as I'm not a programmer
also, I haven't checked the math.

```

<script type="text/javascript" language="javascript" charset="utf-8">

function output(){
var a = parseFloat(document.getElementById('vara').value);
var b = parseFloat(document.getElementById('varb').value);
var c = parseFloat(document.getElementById('varc').value);
var d = (a+b);
var e = (a-b);
var f = ((c)*2);
var g = ((d)*1.57);
var h = Math.pow((e),2);
var i = ((h)/(f*2));

document.getElementById('result').innerHTML = f + g + i;

}
</script>

```



you  used parseFloat() but apparently without understanding what it does. or why you might nred it.
also, your "function" is quite ugly, with those in-function variable assignments for input  in stead of arguments

---

### Post by johnnycatt on 2013-12-09
No, not a homework, porblem.  I manage a small business and I have SEVERAL customers that call me for this information (and several other eqations) for the products we sell them.

I want to add this to my website so I can tell customers try it on the website for themselves!

If I can learn to do this formula, then I can do several others. I keep a few spreadsheets I use a as templates when they call, but this would be SO much easier FOR ME than that! 

I owe you a beer, if this works!!

Thanks for the consideration (I'll check it out!)

---


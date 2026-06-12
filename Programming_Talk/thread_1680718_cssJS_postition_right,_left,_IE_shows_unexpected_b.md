---
title: "css/JS postition right, left, IE shows unexpected behaviour"
date: 2011-02-03
forum: Programming Talk
---

### Post by yc2 on 2011-02-03
Hello,

Sorry for not being able to ask a good question, but this problem has been following me for a long time and I need some fresh thoughts.

2007 I started making a few webpages about Ubuntu in Swedish. The code has gotten pretty ugly over four years. My ambition is that it should work in all five major browsers.

I often use CSS through javascript, like
```
document.getElementById('example_01').style.position = "absolute";
document.getElementById('example_01').style.left = my_text_width + 15 + "px";

```
It has worked OK. On one page you have three layoutalternatives (different width of the text). The text jumps sideways when you press the JS-link.
OK, it is in Swedish and maybe not much use to show here:
[http://e-dog.info/t/63/doc/Ubuntu_installation.php](http://e-dog.info/t/63/doc/Ubuntu_installation.php)

However, for the table of contents (press "innehållsförteckning") something completely unexpected appears in Internet Explorer.

Using for example
position: absolute; left: 800px; (but in JS syntax)
it is impossible to move the div inside the right margin. It sticks to the margin. (It shows just inside the margin but looks like it has divorced from the rest of the text if you use a wide screen.)

I have to use position right and compute from screen-width etc (it seems to work but is quirky too)
position: absolute; right: screen.width - nnn etc etc

_To summarize the problem:_
**For Internet Explorer I cannot position this div (absolute positioning) inside the right margin using CSS attribute "left", I must use "right". No problem in any other browser.**
(I can put it far outside the right margin though. Giving negative arguments will not work either.) Naturally many other divs are positioned properly in IE using position:absolute; and the left attribute. I just seem to have done something stupid to this one without noticing.

The code has slowly developed under four years and is extremely ugly ;) No help supplying it here, I think.

I just wonder if anyone has any input to give.

Thanks.

---

### Post by yc2 on 2011-02-05
Well, I can't say I "solved it" but after several hours of work the page now behaves as I want it.

I finally tried something that sometimes makes Internet Explorer behave. I have noticed it before.

You just send an array of dummy positioning moves and then IE somehow wakes up and performes the last command in the array. (If only the last one had been sent nothing would have happened.) I think I have seen it before, maybe someone else has seen it too?

(I admit the code is not clean but after four years of adding code it sometimes becomes ugly, I think)

```
document.getElementById('example_01').style.right = horis_pos  + "px";	// THIS IS A DUMMY MOVE
document.getElementById('example_01').style.styleFloat = "right";	// THIS IS A DUMMY MOVE
document.getElementById('example_01').style.styleFloat = "none";	// THIS IS A DUMMY MOVE
document.getElementById('example_01').style.left = horis_pos  + "px";	// <--- This is the positioning we want.
```

---


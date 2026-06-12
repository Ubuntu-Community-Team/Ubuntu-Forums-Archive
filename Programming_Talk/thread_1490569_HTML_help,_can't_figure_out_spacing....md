---
title: "HTML help, can't figure out spacing..."
date: 2010-05-22
forum: Programming Talk
---

### Post by talz13 on 2010-05-22
I'm trying to get the list of links along the top to "get back into its home" like it was before I added the drop-down menu to the "services" link.  I have already tried adding up the widths of all the images, and everything adds up to 800 (the width of the parent, I believe)



[http://hollyhilltest2.talz13.com/summer-camp/](http://hollyhilltest2.talz13.com/summer-camp/)



Currently incorrect rendering:
[IMG]http://i50.tinypic.com/2agw1mc.jpg[/IMG]

Correct:
[IMG]http://i46.tinypic.com/2zyc1w1.jpg[/IMG]

---

### Post by KdotJ on 2010-05-22
Have you accounted for the margins and padding in the css? Assuming you have done it this way...

---

### Post by talz13 on 2010-05-22
You got me thinking about the CSS... there were a couple things in the drop-down code that I got that were defined as block level.  I tried playing around with changing it to inline, but didn't get real far.  I got it to be on the same line, but it was stuck at the beginning of the line, before everything else.

Web Devloper extension in firefox tells me:
Normal image links that were there already:
{etc.} > td .nav > a > img

My offending UL image link with drop down:
{etc.} > td .nav > ul #sddm > li > a > img

This is the CSS code that I was playing with (hence the commented lines) for the drop-down menu:
```
#sddm
{	margin: 0;
	padding: 0;
	/*display: inline;*/
	z-index: 30}

#sddm li
{	margin: 0;
	padding: 0;
	list-style: none;
	float: left;
	font: bold 11px arial}

#sddm li a
{	display: block;
	/*display: inline;*/
	margin: 0;
	padding: 0;
	/*width: 60px;*/
	/*width: 287px;*/
	/*background: #5970B2;*/
	background: #FFFFFF;
	color: #FFF;
	text-align: center;
	text-decoration: none}

#sddm li a:hover
{	/*background: #49A3FF*/
	background: #FFFFFF}

#sddm div
{	position: absolute;
	visibility: hidden;
	margin: 0;
	padding: 0;
	/*background: #EAEBD8;*/
	background: #FFFFFF;
	border: 1px solid #5970B2}

	#sddm div a
	{	position: relative;
		display: block;
		/*display: inline;*/
		margin: 0;
		padding: 5px 10px;
		width: auto;
		white-space: nowrap;
		text-align: left;
		text-decoration: none;
		background: #EDEEE0;
		/*color: #2875DE;*/
		color: #000000;
		/*font: 11px arial*/
		font: 18px "Monotype Corsiva", arial;
		font-weight: bold}

	#sddm div a:hover
	{	/*background: #49A3FF;*/
		background: #0066CC;
		color: #FFF}

```

---

### Post by januzi on 2010-05-22
You could add float: left; to the .nav img , .nav a and #sddm

---


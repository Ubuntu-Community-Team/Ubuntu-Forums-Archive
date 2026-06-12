---
title: "html beginner, rendering issue"
date: 2007-05-21
forum: Programming Talk
---

### Post by mills on 2007-05-21
hi all,

thought id start learning html yesterday and iam stuck already,
i cant figure out how to get the text on the right of the table to go below it,
iam sure its easy but i dont  i have the skills yet to work it out

```
<html>
<head>
<title>Lists</title>
<link rel=stylesheet href="style.css" type="text/css">
</head>

<body class="background">
<div align="left"><b><h1>LISTS</h1></b></div><br><br>
To create a <b>bulleted list</b> you need to add a &lt;<b>ul</b>&gt; <br><br>
<b>numbered lists</b> have &lt;<b>ol</b>&gt; tags instead of &lt;<b>ul</b>&gt; tags.<br><br>
To seperate <b>single list</b> items use &lt;<b>li</b>&gt; and &lt;<b>/li</b>&gt; tags.<br><br><br><br>

<div class="sublines">Bulletted lists</div> have the following options;<br>
Disc<br>
circle<br>
square<br><br><br><br>

<div class="sublines"> look at these examples</div><br>

<Table cellpadding=2 border=2 align="left">
<tr>
<td><br><br>&lt;li&gt;text&lt;/li&gt; =<br>
	&lt;li&gt;text&lt;/li&gt; =<br>
	&lt;li&gt;text&lt;/li&gt; =<br></td>
		<td>Makes a bulleted list using<br> the defualt bullet type<br>
		<ul>
		<li>text</li>
		<li>text</li>
		<li>text</li></ul></td></tr>
		
<tr>
<td><br>&lt;ul type="circle"&gt; =<br>
	&lt;ul type="circle"&gt; =<br>
	&lt;ul type="circle"&gt; =<br></td>
		<td>makes a list using circles<br>
		<ul type="circle">
		<li>text</li>
		<li>text</li>
		<li>text</li></ul></td></tr>
<tr>
<td><br>&lt;ul type="square"&gt;</td>
		<td>starts a bulleted<br>list using squares<br>
		<ul type="square">
		<li>text</li>
		<li>text</li>
		<li>text</li></ul></td></tr>
</table>

<br>
<br>
<div class="sublines">Numbered lists</div><br><br>
This page shows how to make different kinds of numbered lists.<br>
You have the following number of options<br><br>

<ul>
<li>Plain numbers</li>
<li>Capitol Letters</li>
<li>Small Letters</li>
<li>Capitol Roman Letters</li>
<li>Small Roman Letters</li>
<ul>

<br<br>
In addition to these options you can specify at which number the list should start.<br>
The defualt start value for numbered lists is at number one (or the letter A).<br><br>
Look at these examples to see the detailed syntax.<br>
</body>
</html>
```

the **Numbered list** part and everything below renders to the right of the table how do i get it below the table?

 iam  kindof ripping off  echoecho.com  just thought the best way to learn would be to make my own tutorial even if it is someone elses, if ya get what i mean,

---

### Post by Blacktalon on 2007-05-21
umm...wow, what did you create it in Frontpage?  There is a bunch of crap in the code from what I can tell means nothing but cluttering up the code. 

Also please be specifice on what you are actually wanting your code to do.....And also please post your CSS file so we can see what exactly you are trying to do in case there is some error inside your CSS code.

---

### Post by mills on 2007-05-21
i made it in gedit,

BODY {background-color:#a3a6ab;}
.headlines, .sublines, infotext {font-face:arial; color:black; font-weight:bold; font-style:italic;}
.headlines {font-size:14pt;}
.sublines {font-size:12pt;}
.infotext {font-size: 10pt;}

iam just trying to make a little tutorial as iam learning, nothing spectacular and nothing that will ever go out on the web

i want this part

> <div class="sublines">Numbered lists</div><br><br>
This page shows how to make different kinds of numbered lists.<br>
You have the following number of options<br><br>

<ul>
<li>Plain numbers</li>
<li>Capitol Letters</li>
<li>Small Letters</li>
<li>Capitol Roman Letters</li>
<li>Small Roman Letters</li>
<ul>

<br<br>
In addition to these options you can specify at which number the list should start.<br>
The defualt start value for numbered lists is at number one (or the letter A).<br><br>
Look at these examples to see the detailed syntax.<br>
</body>
</html>

to appear below the table, at the moment it renders to the right

> There is a bunch of crap in the code from what I can tell means nothing but cluttering up the code. 
is it really that bad lol

---

### Post by mills on 2007-05-21
figured it out
it was the align="left" part in the table declaration

<Table cellpadding=2 border=2 align="left">

took it out and all is good

this html thing is quite good, i think it might catch on:p

---

### Post by tturrisi on 2007-05-21
the table is lft of the lists because you are aligning the table left!
Don't use align="left anymore, use css to align text in table cells.
Don't put text on a page with no tags around it, use the <p> tag at least.
And get in the habit of referring to lists as Unordered and Ordered lists, because the style of the bullet or numbers can be change to almost anything using css, even images as list style markers!
Here's a good place tpo start learning html & css:
[http://www.w3schools.com/](http://www.w3schools.com/)
and good basic tips here:
[http://www.w3.org/QA/Tips/](http://www.w3.org/QA/Tips/)

```
<html>
<head>
<title>Lists</title>
</head>

<body class="background">
<h1>LISTS</h1>
<p>To create an <b>unordered list</b> you need to add a &lt;<b>ul</b>&gt;</p>
<p><b>ordered lists</b> have &lt;<b>ol</b>&gt; tags instead of &lt;<b>ul</b>&gt; tags.</p>
<p>To seperate <b>single list</b> items use &lt;<b>li</b>&gt; and &lt;<b>/li</b>&gt; tags.</p>

<h2>Unordered Lists</h2>
<p>have the following options:<br>
disc<br>
circle<br>
square</p>

<h3>Examples</h3>

<table border="2">
<tr>
<td style="text-align:center; vertical-align:middle;">&lt;li&gt;text&lt;/li&gt; =<br>
	&lt;li&gt;text&lt;/li&gt; =<br>
	&lt;li&gt;text&lt;/li&gt; =<br></td>
		<td style="width:200px;">Makes an unordered list using the defualt bullet type<br>
		<ul>
		<li>text</li>
		<li>text</li>
		<li>text</li></ul></td></tr>
		
<tr>
<td style="text-align:center; vertical-align:middle;">&lt;ul type="circle"&gt; =<br>
	&lt;ul type="circle"&gt; =<br>
	&lt;ul type="circle"&gt; =<br></td>
		<td style="width:200px;">makes an unordered list using circles<br>
		<ul type="circle">
		<li>text</li>
		<li>text</li>
		<li>text</li></ul></td></tr>
<tr>
<td style="text-align:center; vertical-align:middle;">&lt;ul type="square"&gt;</td>
		<td style="width:200px;">makes an unordered list using squares<br>
		<ul type="square">
		<li>text</li>
		<li>text</li>
		<li>text</li></ul></td></tr>
</table>


<h2>Ordered Lists</h2>
<h3>How to make different kinds of ordered lists.</h3>
You have the following options:</p>

<ul>
<li>Plain numbers</li>
<li>Capitol Letters</li>
<li>Small Letters</li>
<li>Capitol Roman Letters</li>
<li>Small Roman Letters</li>
</ul>

<p>In addition to these options you can specify at which number the list should start.<br>The defualt start value for numbered lists is at number one (or the letter A).</p>
<p>Look at these examples to see the detailed syntax.</p>
</body>
</html>
```

---

### Post by mills on 2007-05-21
nice links tturisi, bookmarked them both

and yeah i definitely need to look into css more, the first I'd heard about it was just a few hours ago so lots to learn

and ordered and unordered lists make much more sense, ill have forget about echoecho ;)

cheers for the tips, appreciated

---

### Post by tturrisi on 2007-05-21
also, using tags instead of plain text will eliminate the need for all the <br> tags.
have fun!
this is in my home office:
[www.turrisi.org](www.turrisi.org)

---

### Post by Mirrorball on 2007-05-22
Before you write any code, please read this:
[Developing with web standards](http://www.456bereastreet.com/lab/developing_with_web_standards/)
We need to start making better sites!

---


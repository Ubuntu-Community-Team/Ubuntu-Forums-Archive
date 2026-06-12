---
title: "include() problem with encoding?"
date: 2011-01-11
forum: Programming Talk
---

### Post by vuckovikmarko on 2011-01-11
I've been using Wamp for Windows before, but now i switched to Lampp on Ubuntu. The web page that i was creating, is not working properly on Lampp on Ubuntu. I am from Macedonia, and i use Macedonian keyboard layout, but i think that this post will be helpful to everyone who is using layout different from EN one. Anyway this is the problem: 

I try to include file using include() php function. This is the code in the file named header.inc (it's the main menu):
> 

_header.inc_

<ul id="menu">
<li id="home"><a href="index.php"><b>**&#1044;&#1086;&#1084;&#1072;**</b></a></li>
<li id="single"><a href="#"><b>**&#1052;&#1086;&#1077; CV**</b></a></li>
<li id="dropdown"><a href="primeri.php"><b>**&#1055;&#1088;&#1080;&#1084;&#1077;&#1088;&#1080;**</b></a></li>
<li id="contact"><a href="#"><b>**&#1050;&#1086;&#1085;&#1090;&#1072;&#1082;&#1090;**</b></a></li>
</ul>

As you can see in the menu there are some words written in Macedonian language, the bold ones. 

in my index.php script, i put 

<?php include ("header.inc"); ?>

And on the browser i see this screenshot
[IMG]http://lh3.ggpht.com/_762pwf5JP_M/TSyFKNdikcI/AAAAAAAAAFs/fPgN43yGb3s/Slika1.png[/IMG] 

As you can see, instead of the Macedonian words, i see ???.  
On WAMP on Windows, i dont have this problem. Everything is ok and i see the Macedonian words as they are.

The header.inc file is saved as utf8 encoding. 

Please HELP!

---

### Post by v8YKxgHe on 2011-01-11
What charset are you sending the HTML as to the browser? You'll normally want something like this in your PHP:

```
<?php header('Content-Type: text/html; charset=utf-8'); ?>
```

---

### Post by vuckovikmarko on 2011-01-11
Thanks for your answer, but I copied and pasted your code at the start of my index.php page, and nothing happened. The question marks are still there. 

If this helps i checked with file [file name] both of my files (thats header.inc and index.php) and this is what i get back:

**header.inc: UTF-8 Unicode (with BOM) text, with CRLF line terminators **

---

### Post by Arndt on 2011-01-11
> **vuckovikmarko said:**
> I've been using Wamp for Windows before, but now i switched to Lampp on Ubuntu. The web page that i was creating, is not working properly on Lampp on Ubuntu. I am from Macedonia, and i use Macedonian keyboard layout, but i think that this post will be helpful to everyone who is using layout different from EN one. Anyway this is the problem: 

I try to include file using include() php function. This is the code in the file named header.inc (it's the main menu):


As you can see in the menu there are some words written in Macedonian language, the bold ones. 

in my index.php script, i put 

<?php include ("header.inc"); ?>

And on the browser i see this screenshot
[IMG]http://lh3.ggpht.com/_762pwf5JP_M/TSyFKNdikcI/AAAAAAAAAFs/fPgN43yGb3s/Slika1.png[/IMG] 

As you can see, instead of the Macedonian words, i see ???.  
On WAMP on Windows, i dont have this problem. Everything is ok and i see the Macedonian words as they are.

The header.inc file is saved as utf8 encoding. 

Please HELP!

Does it work if you have Macedonian words in plain html, bypassing the php code?

---

### Post by vuckovikmarko on 2011-01-11
I am not sure if you mean like this 

> 
<html>
<body>

Macedonian font here

</body>
</html>


It works like this. Also it's working like this

> 
<html>
<body>

<?php
echo "Macedonian font here";
?>

</body>
</html>


It doesn't work if i try to include file, which can be php,html,inc... This codes will not write Macedonian text if i try to include them on some other script.

---

### Post by v8YKxgHe on 2011-01-12
Please paste your full scripts code.

---

### Post by vuckovikmarko on 2011-01-12
The index.php page

```

<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>CV - &#1044;&#1086;&#1084;&#1072;</title>
<link href="CSS/cv.css" rel="stylesheet" type="text/css">
</head>

<body>
<?php header('Content-Type: text/html; charset=utf-8'); ?>
<?php session_start(); ?>
<div class="container">
  <div class="header" align="center">
    <?php include ("header.inc"); ?> //here is the problem
  <!-- end .header --></div>

<?php echo "macedonian text here"; ?> // this will work
.
.
.

<!-- end .container --></div>
</body>
</html>
```

this is the header.inc page

```


<ul id="menu" lang="mk">
<li id="home" lang="mk"><a href="index.php"><b>&#1044;&#1086;&#1084;&#1072;</b></a></li>
<li id="single"><a href="#"><b>&#1052;&#1086;&#1077; CV</b></a></li>
<li id="dropdown"><a href="primeri.php"><b>&#1055;&#1088;&#1080;&#1084;&#1077;&#1088;&#1080;</b></a></li>
<li id="contact"><a href="#"><b>&#1050;&#1086;&#1085;&#1090;&#1072;&#1082;&#1090;</b></a></li>
</ul>
```

---


---
title: "php site working on all broswers except I.E"
date: 2011-07-14
forum: Programming Talk
---

### Post by gillespiea on 2011-07-14
Hi folks, i've been making a php website and using google chrome to test it. Seeing as i run Ubuntu i never tested it on I.E

After putting up a beta for some people to test the running parts, a friend running Windows told me that it doesn't display anywhere near properly.

I've read that if you don't tell i.e the DOCTYPE it wont work properly. but what one do i use?! there are so many and i've never even thought about it before.

My theme.php (which almost all pages use) is coded as such:
[PHP]<link rel="stylesheet" type="text/css" href="style.css" />
<?php 
include "menu.php";
include_once "config.php";
include_once "title.php";
include "newmember.php";

?>
<?php
function ae_detect_ie()
{
    if (isset($_SERVER['HTTP_USER_AGENT']) && 
    (strpos($_SERVER['HTTP_USER_AGENT'], 'MSIE') !== false))
        return true;
    else
        return false;
}
?>
<?php  if (ae_detect_ie()) { 
$intro = "<h1>OOPS!</h1>It seems, that your are using Microsofts Internet Explorer and this website, sadly, will not display properly.
Why not to switch to standard-complaint brower, like 
<a href=\"http://www.mozilla.com/firefox/\">Firefox</a>?
or <a href=\"http://www.google.com/chrome/\">Google chrome</a> (recommended)
"; }
else {$intro = $intro;} 
?> 
<?php $mainb = "<html>

<head>
<title>$ptitle</title>
<link rel=\"stylesheet\" type=\"text/css\" href=\"style.css\" />
<script type=\"text/javascript\" src=\"js/prototype.js\"></script>
<script type=\"text/javascript\" src=\"js/scriptaculous.js?load=effects,builder\"></script>
<script type=\"text/javascript\" src=\"js/lightbox.js\"></script>
</head>
<body>
$newmem
<img src=\"img/VFR400.jpg\" id=\"beta\">
<table summary=\"main\" id=\"main\">
<tr>
<td id=\"lftbrd\"> &nbsp;</td>
<td id=\"intro\">$intro</td>

<td id=\"vid\"><h1>Video of the week</h1><iframe width=\"300\" height=\"200\" src=\"http://www.youtube.com/embed/PFvwymR9U0o?wmode=transparent\" frameborder=\"0\" allowfullscreen></iframe></td>
<td id=\"rgtbrd\"> &nbsp;</td>
</tr>

<tr>
<td id=\"lftbrdm\"></td>
<td id=\"menu\" colspan=\"2\"> $menu_block </td>
<td id=\"rgtbrdm\"></td>
</tr>

<tr>
<td id=\"lftbrd\"></td>
<td id=\"news\" colspan=\"2\">";


$maine = "
</td>
<td id=\"rgtbrd\"></td>
</tr>
</table>
<table align=\"right\" id=\"log\">
<tr><td>
<iframe src=\"log/index.php\" id=\"log\"></iframe>
</td></tr>
</table>
</body>
</html>"
?>[/PHP]

and my style sheet is:
```
#pages
{
	margin:0;
	padding: 0;
	list-style: none;
}
#prev
{
	list-style: none;
	display: block;
	float: left;
}
#pagenumber
{
	list-style: none;
	text-align: center;
}
#nextpage
{
	list-style: none;
	float: right;
}
#lastpage
{
	list-style: none;
	
}

.eqr
{
	float: right;
}
#lightbox{	position: absolute;	left: 0; width: 100%; z-index: 100; text-align: center; line-height: 0;}
#lightbox img{ width: auto; height: auto;}
#lightbox a img{ border: none; }

#outerImageContainer{ position: relative; background-color: #fff; width: 250px; height: 250px; margin: 0 auto; }
#imageContainer{ padding: 10px; }

#loading{ position: absolute; top: 40%; left: 0%; height: 25%; width: 100%; text-align: center; line-height: 0; }
#hoverNav{ position: absolute; top: 0; left: 0; height: 100%; width: 100%; z-index: 10; }
#imageContainer>#hoverNav{ left: 0;}
#hoverNav a{ outline: none;}

#prevLink, #nextLink{ width: 49%; height: 100%; background-image: url(data:image/gif;base64,AAAA); /* Trick IE into showing hover */ display: block; }
#prevLink { left: 0; float: left;}
#nextLink { right: 0; float: right;}
#prevLink:hover, #prevLink:visited:hover { background: url(/images/prevlabel.gif) left 15% no-repeat; }
#nextLink:hover, #nextLink:visited:hover { background: url(/images/nextlabel.gif) right 15% no-repeat; }

#imageDataContainer{ font: 10px Verdana, Helvetica, sans-serif; background-color: #fff; margin: 0 auto; line-height: 1.4em; overflow: auto; width: 100%	; }

#imageData{	padding:0 10px; color: #666; }
#imageData #imageDetails{ width: 70%; float: left; text-align: left; }	
#imageData #caption{ font-weight: bold;	}
#imageData #numberDisplay{ display: block; clear: left; padding-bottom: 1.0em;	}			
#imageData #bottomNavClose{ width: 66px; float: right;  padding-bottom: 0.7em; outline: none;}	 	

#overlay{ position: absolute; top: 0; left: 0; z-index: 90; width: 100%; height: 500px; background-color: #000; }

#nextprev
{
	text-align: center;
}

.admin
{
	text-align: right;
	padding-right: 10px;
}

#newposts
{
	width: 20px;
}
#topic

{
	background: #ccc;
	color: #000;
	vertical-align: text-top;
	font-size: 12px;
	padding: 10px;
	border: 1px solid white;
	border-radius: 15px;
	width: 50%;
}
#upload

{
	background: #ccc;
	color: #000;
	vertical-align: text-top;
	font-size: 12px;
	padding: 10px;
	border: 1px solid white;
	border-radius: 15px;
	width: 100%;
	height: 100%;
}
#quote
{
	background: #bbb;
	color: #fff;
	font-size: 12px;
	padding: 10px;
	border: 5px inset #aaa;
	border-radius: 15px;
}
#right
{
	float: right;
}
#eventa

{
	background: #ccc;
	color: #000;
	vertical-align: text-top;
	text-align: center;
	font-size: 12px;
	padding: 10px;
	border: 1px solid white;
	border-radius: 15px;
	width: 10%;
}
#del
{
	float: right;
}
#eventd

{
	background: #ccc;
	color: #000;
	vertical-align: text-top;
	text-align: center;
	font-size: 12px;
	padding: 10px;
	border: 1px solid white;
	border-radius: 15px;
	width: 30%;
}
#event

{
	background: #ccc;
	color: #000;
	vertical-align: text-top;
	font-size: 12px;
	padding: 10px;
	border: 1px solid white;
	border-radius: 15px;
	width: 70%;
}
#event a:link
{ 
	color: #000;
	text-decoration: none;
}

#event a:hover
{
	color: #555;
		
}

#forum

{
	background: #ccc;
	color: #000;
	vertical-align: text-top;
	font-size: 12px;
	padding: 10px;
	border: 1px solid white;
	border-radius: 15px;
	width: 100%;
}
#forum a:link
{ 
	color: #000;
	text-decoration: none;
}

#forum a:hover
{
	color: #555;
		
}

#forumtd
{
	width: 50%;
}
#lastposttd
{
	width: 16.7%;
	height: 50px;
	text-align: center;
	border: 2px solid white;
	border-radius: 15px;
	
}
#forumposttd
{
	
	background: #ccc;
	padding: 15px;
	border: 2px solid white;
	vertical-align: text-top;
	border-radius: 15px;
	
}
#forumusertd
{
	width: 90px;
	background: #ccc; 
	padding: 15px;
	border: 2px solid white;
	border-radius: 15px;
	vertical-align: text-top;
}
body
{
	background:url(img/logo.png) bottom left no-repeat #000;
	background-attachment: fixed;
	font-family: Verdana;
	
}
#mem
{
	position: fixed;
	top: 0px;
	left: 0px;
	color: #ccc;
	background: #000;
	padding: 5px;
	border-radius: 0 0 15px 0;
	border-bottom: 2px solid white;
	border-right: 2px solid white;
}
#log
{
	position: absolute;
	top: 0px;
	right: 0px;
	
	position: fixed;
	color: #000;
	vertical-align: text-top;
	font-size: 12px;
	height: 900px;
	border-collapse: collapse;
	
} 
iframe
{
	border: 0px;
	border-collapse: collapse;
}
#beta
{
	float: right;	
	position: fixed;
	bottom: 0;
	right: 0;
}

#main
{
	color: #000;
	border 0px;
	padding: 0;
	margin: auto;
	position: absolute;
	top: 0;
	right: 0;
	left: 0;
	width: 55%;
	height: 1000px;
	background-color: #fff;
	border-collapse: collapse;
	
}

#lftbrd
{
	background:url('img/borderlft.jpg') top left;
	background-repeat:x;
	width: 6px;
	margin: 0px;
	padding: 0px;
	border: 0px;
	vertical-align: text-top;
}

#rgtbrd
{
	background:url('img/borderrgt.jpg') top left;
	background-repeat:x;
	width: 6px;
	margin: 0px;
	padding: 0px;
	border: 0px;
}
#vid
{
	background-color: #fff;
	border: 0px;
	margin: 0px;
	padding: 10px;
	width: 302px;
	height: 220px;
	
}


	
#menu
{
	height: 40px;
	background-image: url('img/menubg.jpg');
	text-align: center;
	font-variant: small-caps;
	color: #fff;
	
	text-shadow: #000 1px -1px -2px;
	list-style: none;
	
} 



#menu a:link
{ 
	color: #fff;
	text-decoration: none;
}

#menu a:hover
{
	color: #ddd;
		
}

#menu :visited
{ 
	color: #fff;
}
#lftbrdm
{
	background:url('img/borderlftm.png') top left;
	background-repeat:x;
	width: 6px;
	margin: 0px;
	padding: 0px;
	border: 0px;
}

#rgtbrdm
{
	background:url('img/borderrgtm.png') top left;
	background-repeat:x;
	width: 6px;
	margin: 0px;
	padding: 0px;
	border: 0px;
}
#news
{
	background: #fff;
	color: #000;
	vertical-align: text-top;
	font-size: 12px;
	padding: 10px;
	width: 100%;
} 
#news :link
{
	color: #000;
}
#news :visited
{
	color: #000;
}
#intro
{
	width: 614px;
	font-size:10px;
	text-align: justify;
	padding: 10px;
}

h1
{
	font-size: 14px;
}
#header
{
	vertical-align: text-top;
}





```

---

### Post by ruffEdgz on 2011-07-14
Just wondering but did you mean to place a != instead of a !== in the function ae_detect_ie()?
```

function ae_detect_ie() 
{ 
    if (isset($_SERVER['HTTP_USER_AGENT']) &&  
    (strpos($_SERVER['HTTP_USER_AGENT'], 'MSIE') **!=** false)) 
        return true; 
    else 
        return false; 
}

```
Want to make sure if that was a typo or whats on the code.

Cheers!

---

### Post by juancarlospaco on 2011-07-14
Just put a link to Chrome Frame...

---

### Post by pbrane on 2011-07-14
> **juancarlospaco said:**
> Just put a link to Chrome Frame...

+1

IE is not a standards compliant browser.

I'm pretty sure ruffEdgz is right about the syntax error.

---

### Post by juancarlospaco on 2011-07-14
> **pbrane said:**
> 
IE is not a standards compliant browser.


+1
Even the most modern versions of IE dont know whats <canvas> or .SVG or WebP or WebM or Sockets or (...)

---

### Post by gillespiea on 2011-07-14
never heard of that before. Thanks for letting me know!
i'll try it out and let you know how it goes.

---

### Post by gillespiea on 2011-07-14
> **ruffEdgz said:**
> Just wondering but did you mean to place a != instead of a !== in the function ae_detect_ie()?
```

function ae_detect_ie() 
{ 
    if (isset($_SERVER['HTTP_USER_AGENT']) &&  
    (strpos($_SERVER['HTTP_USER_AGENT'], 'MSIE') **!=** false)) 
        return true; 
    else 
        return false; 
}

```
Want to make sure if that was a typo or whats on the code.

Cheers!
That piece of code was taken from a tutorial. Only part in that page that wasn't written by me lol. I'm surprised you never picked up on other problems!

---

### Post by juancarlospaco on 2011-07-14
> **gillespiea said:**
> never heard of that before. Thanks for letting me know!


[http://code.google.com/chrome/chromeframe/](http://code.google.com/chrome/chromeframe/)

Use the <-- [if lte IE 7]->  TAG thingy

---

### Post by Barrucadu on 2011-07-14
You should use === and !== for strpos. [http://php.net/manual/en/function.strpos.php](http://php.net/manual/en/function.strpos.php)

You could shorten your function to:

[php]
function ae_detect_ie ()
{
  return (strpos ($_SERVER['HTTP_USER_AGENT'], 'MSIE') !== false);
}
[/php]

As $_SERVER['HTTP_USER_AGENT'] will always be set (unless you run it with `php` from the command line, or something)

---

### Post by gillespiea on 2011-07-15
Thanks very much folks! chrome frame has done the job wonderfully!

---


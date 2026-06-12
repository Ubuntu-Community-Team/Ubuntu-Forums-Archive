---
title: "[SOLVED] Need some web design help."
date: 2008-01-31
forum: Programming Talk
---

### Post by spyder0101 on 2008-01-31
I'm a novice web designer playing around with using css for positioning.  I'm having a problem with one of my templates :(.  It work fine in FF, but in IE the right box shifts down below the left box and is not indented.  Can anyone help me figure out why? :confused:

Here is my css:

```

ul{
	list-style-type:none;
}

#Container {
	left: 0px;
	top: 0px;
	width: 820px;
	position: relative;
	margin-right: auto;
	margin-left: auto;
}

#header {
	float: left;
	left: 0px;
	top: 0px;
	width: 820px;
	height: 364px;
	background-image: url('images/head1.png');
}

#header ul.navi{
	width: 750px;
	display: block;
	position: absolute;
	top: 330px;
	left: 80px;
	padding: 0;
	margin: 0;
	background: none;
}

#header ul.navi li{
	border-width: 1px;
	height: 22px;
	padding: 0 18px 0 5px;
	margin: 0;
	display: block;
	float: left;
}

#header ul.navi li.li1{
	background:none;
	height:22px;
	padding:0 14px 0 5px;
	margin:0;
	display:block;
	float:left; 
}

#header ul.navi li a{
	font: 12pt Arial, Helvetica, sans-serif;
	color: #000000;
	text-decoration: none;
	text-indent: 0px;
	padding: 0 0 0 33px;
	font-weight: bold;
	margin: 0;
	width: inherit;
	letter-spacing: -1px;
}

#header ul.navi li a:hover{
	color: #000000;
	text-decoration: none;
}

#left {
	float: left;
	left: 0px;
	top: 384px;
	width: 266px;
}

#left h2{
	font: 30px/24px "Calisto MT";
	color: #000000;
	font-weight: normal;
	display: block;
	letter-spacing: -1px;
	word-spacing: 0em;
	text-indent: 0px;
	margin-top: 0;
	margin-right: 0;
	margin-bottom: 10px;
	padding-top: 0px;
	padding-left: 55px;
}

#left p{
	background: no-repeat;
	color: #000000;
	padding: 0 0 0 55px;
	width: 190px;
	display: block;
	font: 13px/20px "Trebuchet MS";
	margin-top: 0;
	margin-right: 0;
	margin-bottom: 0;
	letter-spacing: 0px;
}

#left p span{
	color: #000000;
	font-weight: bold;
	font-size: 16px;
	letter-spacing: -1px;
}

#left p span.bg{
	color: #000000;
}

#left p a{
	font: 13px/12px "trebuchet MS";
	font-weight: normal;
	color: #000000;
	text-decoration: underline;
	padding-top: 0;
	padding-right: 0;
	padding-bottom: 0;
}

#left p a:hover{
	background: no-repeat;
	color: #000000;
	font-weight: normal;
}

#right {
	float: left;
	left: 266px;
	top: 384px;
	width: 554px;
}

#right h2{
	font: 30px/24px "Calisto MT";
	color: #000000;
	font-weight: normal;
	display: block;
	letter-spacing: -1px;
	word-spacing: 0em;
	text-indent: 0px;
	margin-top: 0;
	margin-right: 0;
	margin-bottom: 10px;
	padding-top: 0px;
	padding-left: 20px;
}

#right p{
	background: no-repeat;
	color: #000000;
	padding: 0 0 0 20px;
	width: 490px;
	display: block;
	font: 13px/20px "Trebuchet MS";
	margin-top: 0;
	margin-right: 0;
	margin-bottom: 0;
	letter-spacing: 0px;
}

#right p span{
	color: #000000;
	font-weight: bold;
	font-size: 16px;
	letter-spacing: -1px;
}

#right p span.bg{
	color: #000000;
}

#right p a{
	font: 13px/12px "trebuchet MS";
	font-weight: normal;
	color: #000000;
	text-decoration: underline;
	padding-top: 0;
	padding-right: 0;
	padding-bottom: 0;
}

#right p a:hover{
	background: no-repeat;
	color: #000000;
	font-weight: normal;
}

body {
	background-color: #99ccff;
	margin: 0px;
	border: 0px;
}

```

And here is my html:

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>TITLE</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
<link rel="stylesheet" type="text/css" href="css.css" />
</head>
<body>
<div id="Container">
	<div id="header">
		&nbsp;<ul class="navi">
			<li><a href="#">link</a></li>
			<li><a href="#">link</a></li>
			<li><a href="#">link</a></li>
			<li><a href="#">link</a></li>
			<li><a href="#">link</a></li>
			<li><a href="#">link</a></li>
		</ul>
	</div>

	<div id="left">
		<h2>H2 text</h2><p>A paragraph with<span class="style1">something empathized</span></div>
	</div>

	<div id="right">
		<h2>H2</h2><p>Ptext<span class="style1">span stuff</span> more stuff<br>
		<h2>more titles</h2><p>lots more stuff<br>
		<h2>more titles</h2><p>Tons of misc stuff<br>
	</div>

	<div id="footer-contents">
		<p><span>My Footer™</span></p>
	</div>
</div>
</body>
</html>

```

Thanks in advance

Spyder

---

### Post by kool_kat_os on 2008-01-31
can you post it with a webaddress so we can look at it?

---

### Post by spyder0101 on 2008-01-31
I wish I could, but I can't until Monday, which is when I need it.  However I found the error, I closed the left div twice, closing my container in the process.  Thanks to everyone that looked at the code though.

Spyder

---


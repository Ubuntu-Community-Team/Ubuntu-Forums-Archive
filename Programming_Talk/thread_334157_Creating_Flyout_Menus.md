---
title: "Creating Flyout Menus"
date: 2007-01-08
forum: Programming Talk
---

### Post by SuperMike on 2007-01-08
I'm trying to create flyout menus to enhance this howto article:

[http://www.ubuntuforums.org/showthread.php?t=333862]("http://www.ubuntuforums.org/showthread.php?t=333862")

But for some reason I can't add an Edit menu beside it and it goes under it instead. Do you know what might be the issue? In general I'm looking for menus that sort of look like what you might see in an application except that you don't have to click File, Edit, and so on, to see the menu. Doing it purely in CSS would be ideal because it's cleaner, and since I'm doing an XUL app on Firefox, I won't need to worry about Internet Exploder.

```
<html>
<head>
<title>Pure CSS Menus</title>
<style type="text/css">
body {
	background: #f7f7f7;
}
ul {
	padding: 0; 
	margin: 0; 
	/* border-bottom: 1px solid silver; */
}
ul li {
	list-style-type: none; 
	border-width: 1px 1px 0 3px;
  	position: relative; 
  	margin: 0;
  	padding: 0;
}
ul ul {
	display: none;
}
ul li:hover > ul {
	display: block; 
	position: absolute; 
	top: -1px; 
	left: 100%;
	border: 1px solid silver;
}
li a {
	display: block; 
	padding: 5px 7px;
	text-decoration: none;
	background: #f7f7f7;
	color: black;
	font-family: Arial,sans;
	font-size: 12px;
	cursor: default;
}
ul#topmenu {
	width: 6em;
}
ul#topmenu > li:hover > ul {
	width: 10em;
	top: 1.5em;
	left: -3px;border: 1px solid silver;
}
ul ul {
	width: 10em;
}

div#menus {
	border-bottom: 1px solid Gainsboro;
}
li#break {
	color: Gainsboro;
	height: 1px;
	margin-left: 6px;
	margin-right: 6px;
	border-top: 1px solid silver;
}
li#flyout > a {
	background-image: url('flyout.png');
	background-repeat: no-repeat;
	background-position: right;
}
ul#topmenu a:hover {
	background-color: Gainsboro;
}
</style>
</head>
<body topmargin=0 leftmargin=0 marginwidth=0 marginheight=0>
<div id="menus">
	<ul id="topmenu">
		<li class="sub"><a href="">File</a>
			<ul>
				<li class="sub" id="flyout"><a href="myapp/index.js?mode=new" title="">New</a>
				<ul>
					<li><a href="myapp/index.js?mode=test1" title="">test1</a></li>
					<li><a href="myapp/index.js?mode=test2" title="">test2</a></li>
				</ul>
				</li>
			<li><a href="myapp/index.js?mode=open" title="">Open</a></li>
			<li><a href="myapp/index.js?mode=save" title="">Save</a></li>
			<li id="break"></li>
			<li><a href="myapp/index.js?mode=quit" title="">Quit</a></li>    
		</li>
	</ul>
</div>
</body>
</html>
```

P.S. If you have a way to make the code even tighter, that's way cool too.

---

### Post by Wybiral on 2007-01-08
I don't do much web design, but you're using list's... If I had to guess I would say the list's don't want to be horizontal. But, thats just a guess, like I said... I don't really know how they work.

---

### Post by Tomosaur on 2007-01-08
Yeah I'm fairly sure lists default to vertical, and I don't think there's an option to have them go horizontal. You may wish to try using the 'float' css property to get certain entries in the list to float to the right.

---

### Post by WiseElben on 2007-01-08
There is a way to make the list horizontal. You just need to add: [HTML]display: inline;[/HTML] In the list class, like [FONT="Lucida Console"]#class1 li[/FONT] for example

---

### Post by SuperMike on 2007-01-09
I finally figured out the answer to building application-style menus in CSS.

[http://www.ubuntuforums.org/showpost.php?p=1987954&postcount=8]("http://www.ubuntuforums.org/showpost.php?p=1987954&postcount=8")

This will be useful to new developers who might be using the XUL technique (specified in the article above if you look at the whole thread) to build applications on Linux.

---


---
title: "CSS question"
date: 2010-08-12
forum: Programming Talk
---

### Post by badperson on 2010-08-12
this should be really basic, but...
I have this html:

```
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<link rel="stylesheet" type="text/css" href="css/coffee2.css">
</head>
<body>

<div id="header">
<h1>Coffee Roasting App</h1>
</div>
<div id="subheader">
	<ul>
	<li>Links</li>
	<li>Advanced Search</li>

	</ul>
	
	<div id="searchForm">
		<form id="searchForm" method="get">
		<input type="text" value="search" id="searchField"/>
		<input type="submit" id="searchButton" value="go"/>
		</form>
	</div>
</div>
```

with this css: 

```
body {
	text-align: left;
	color:  #FFFFFF;
	background-color: #736F6E;
	width: 960px;
	font-family: Arial, Tahoma, Verdana;
	line-height: 1em;
	padding: 0px;


}


#header{
	background-color: #5E5A80;
	width:960px;
	height: 120px;
	text-align: center;
	margin-top:0px;
}

#header h1 {
	padding: 50px 0px 0px 0px;
	font-size: 60px;

}
```

the problem is that there is a big space between the top of the page and the #header section...I want the header to be flush at the top of the page. I tried padding and margin stuff in the css...any ideas?
bp

---

### Post by TheOrangePeanut on 2010-08-12
Use a CSS reset.  Something like this:

```

html,body,div,span,p,h1,h2,h3,h4,h5,h6{margin:0;padding:0}

```

Add other elements you use.  The reason for this is that different browsers give elements margin and padding by default and they all differ, so you need to reset it.

---


---
title: "HTML/CSS Menu Woes"
date: 2012-05-08
forum: Programming Talk
---

### Post by andrewbrown22 on 2012-05-08
I'm working on a pretty basic website for someone while trying to teach myself / learn HTML and CSS, etc. I've been able to lay it out essentially the way I'd like it, with a couple exceptions. 

1) The menu I've been able to come up with is not centered in the "menu_wrapper" div it's contained in. I like the way the menu is styled (although basic, it seems like it would be functional) except that I cannot get it centered properly. 

2) The "main" div has a background color applied to it, yet it does not show through. This also happens with the border applied to it. 

3) Quite possibly related to #2, the class defined pageContainer's border does not surround the full content of the page, rather just the upper area. 


I've attached the files to this thread.

I'm completely new at all of this, so any help is appreciated. It's very possible my CSS is not anywhere near optimally written and any suggestions would be great.

---

### Post by cajual on 2012-05-08
This is easier to solve if you show pictures and paste code snippets. No one wants to dive into a zip file.

I've addressed all the issues here (update your css file):

```


@charset "UTF-8";
/* CSS Document */

BODY {
    background-color: #ccc;
    padding: 40px 0;
}

.pageContainer {
    /* This centers the page and makes it 1000px wide */
    width: 1000px;
    margin: auto;
    border: 1px dashed;
    /* Because it isn't a floating layer, so it doesn't contain
    other floating layers -- Best to remove the border */
}

#banner {
    /* This is the required "persistent" banner that spans the
    top of the page at all times */
    position: fixed;
    top:0;
    background-color: #ccf;
    width: 100%;
    height: 30px;
    text-align: right;
    font-family: Arial, sans-serif;
}

#banner img {
    /* This will center any images placed in the banner */
    vertical-align: middle;
}

#logo {
    width: 355px;
    margin-left: auto;
    margin-right: auto;
}

#menu_wrapper {
    width: 100%;
    border: 1px dashed #0099cf;
}

#menu {
}

#menu ul {
    list-style: none;
}

#menu li {
    display: inline;
}

#menu li a {
    margin-right: -4px;
    font-family:Arial;
    font-size:12px;
    text-decoration: none;
    padding:10px;
    background-color: #333333;
    color:#ffffff;
    border-bottom:1px;
    border-bottom-color:#000000;
    border-bottom-style:solid;
}

#menu li a:hover {
    background-color:#8ec63f;
    padding-bottom:10px;
    border-bottom:2px;
    border-bottom-color:#000000;
    border-bottom-style:solid;
    margin:0px -4px -2px 0;
}

#main {
    /* You forgot to float this as well */
    float:left;
    background-color: #ccc; /* Your body color is already #ccc */
    border: 2px #000 solid; /* You forgot a style type (solid) */
}

#left_container {
    width: 650px;
    float: left;
    margin-top: 30px;
    border: thin dashed;
    background-color: #6cd;
    padding: 0 2px 0 2px;
}

#right_container {
    width: 300px;
    float: left;
    margin-top: 30px;
    margin-left: 40px;
}

#box1 {
    border: thin dashed;
    background: #6ce;
}

#box2 {
    margin-top: 20px;
    border: thin dashed;
    background: #6cf;
}

#box1 h1, #box2 h1 {
    font-size: 95%;
}

#footer {
    width: 100%;
    float: left;
    font-size: 75%;
}

p {
    font-family: Arial;
}

h1 {
    font-family: Arial;
}


```

---

### Post by andrewbrown22 on 2012-05-08
Great, thank you very much for the help. I've changed the background of the "main" div and removed some of the borders. However, the menu still seems to be more to the left of the pageContainer.

I've attached a screenshot, and here's the code. 

```
@charset "UTF-8";
/* CSS Document */

BODY {
    background-color: #ccc;
    padding: 40px 0;
}

.pageContainer {
    /* This centers the page and makes it 1000px wide */
    width: 1000px;
    margin: auto;
}

#banner {
    /* This is the required "persistent" banner that spans the
    top of the page at all times */
    position: fixed;
    top:0;
    background-color: #ccf;
    width: 100%;
    height: 30px;
    text-align: right;
    font-family: Arial, sans-serif;
}

#banner img {
    /* This will center any images placed in the banner */
    vertical-align: middle;
}

#logo {
    width: 355px;
    margin-left: auto;
    margin-right: auto;
}

#menu_wrapper {
    width: 100%;
}

#menu {
}

#menu ul {
    list-style: none;
}

#menu li {
    display: inline;
}

#menu li a {
    margin-right: -4px;
    font-family:Arial;
    font-size:12px;
    text-decoration: none;
    padding:10px;
    background-color: #333333;
    color:#ffffff;
    border-bottom:1px;
    border-bottom-color:#000000;
    border-bottom-style:solid;
}

#menu li a:hover {
    background-color:#8ec63f;
    padding-bottom:10px;
    border-bottom:2px;
    border-bottom-color:#000000;
    border-bottom-style:solid;
    margin:0px -4px -2px 0;
}

#main {
    float:left;
    background-color: #6ab;
}

#left_container {
    width: 650px;
    float: left;
    margin-top: 30px;
    background-color: #6cd;
    padding: 0 2px 0 2px;
}

#right_container {
    width: 300px;
    float: left;
    margin-top: 30px;
    margin-left: 40px;
}

#box1 {
    background: #6ce;
}

#box2 {
    margin-top: 20px;
    background: #6cf;
}

#box1 h1, #box2 h1 {
    font-size: 95%;
}

#footer {
    width: 100%;
    float: left;
    font-size: 75%;
}

p {
    font-family: Arial;
}

h1 {
    font-family: Arial;
}
```

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<title>dev</title>
<link href="style.css" rel="stylesheet" type="text/css" />
</head>

<body>

<div id="banner">Required Banner <img src="img/us.gif" width="50" height="28" alt="" />
</div>

<div class="pageContainer">
	<div id="logo"><img src="img/logo1.png" width="355" height="70" />
	</div>

	<div id="menu_wrapper">
	<div id="menu">
		<ul>
			<li><a href="#">The Moringa Story</a></li>
			<li><a href="#">Hear from the Formulator</a></li>
			<li><a href="#">Moringa Research</a></li>
			<li><a href="#">The Zija Story</a></li>
			<li><a href="#">Zija's Product Profiles</a></li>
			<li><a href="#">Zija's Business Testimonials</a></li>
			<li><a href="#">Join Now</a></li>
        </ul>
	</div>
	</div>
	<div id="main">
		<div id="left_container"><h1>Left</h1>
		<p>Content contained in the left div called "left_container"</p>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque gravida, magna ac scelerisque condimentum, felis felis ornare eros, non convallis mauris tortor quis erat. Mauris convallis nisi a mi iaculis at consectetur orci auctor. Nunc imperdiet leo sed nibh placerat pulvinar. Suspendisse convallis ornare turpis, sed mattis nibh laoreet sit amet. Suspendisse posuere vehicula libero, a porttitor augue volutpat vel. Lorem ipsum dolor sit amet, consectetur adipiscing elit. In et lobortis urna. Integer sit amet lorem nunc. Aenean placerat massa non nibh facilisis suscipit. Proin et erat sed massa pellentesque aliquam. Ut vitae turpis dolor, sed hendrerit tortor. Morbi justo turpis, laoreet nec iaculis vitae, adipiscing vel sem. Vestibulum sagittis, risus nec sagittis pellentesque, elit ante sollicitudin nibh, id dignissim purus leo nec mi.
<br /><br />
Nulla metus sapien, imperdiet vel convallis a, hendrerit quis purus. Aenean at orci tincidunt libero fringilla scelerisque faucibus eu justo. Ut volutpat, urna non condimentum lobortis, nibh lorem scelerisque ligula, ut tincidunt enim tellus quis sem. Morbi id turpis est, eleifend volutpat lorem. Sed lacinia, ipsum eu varius tincidunt, nisi ipsum porta libero, vel tempus libero nibh sed risus. Suspendisse sit amet blandit elit. Duis rhoncus leo mattis odio posuere vitae aliquam mauris porta.
</p></div>
		<div id="right_container">
			<div id="box1"><h1>Box 1</h1>
			<p>Box 1 contents.</p></div>
			<div id="box2"><h1>Box 2</h1>
			<p>Box 2 contents.</p></div>
		</div>
	</div>
	<div id="footer">Footer</div>
</div>
</body>
</html>
```

---


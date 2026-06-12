---
title: "php includes - background-image not rendering"
date: 2011-05-29
forum: Programming Talk
---

### Post by bcn17 on 2011-05-29
Hello, I am very new to PHP and have quite a perplexing problem. My background-image will not render.

I am using an include in the <head> section of my "index.php" file to link a "style.php" file that has a link to my CSS stylesheet "main.css". 

**index.php**
```
<head><?php include("style.php"); ?></head>
```

**style.php**
```
<link rel="stylesheet" type="text/css" href="css/main.css" />
```

So far I have had all of my CSS render flawlessly except my background-image. For testing purposes I am copying the directory I am working in into my apache webserver folder and pointing the browser to "localhost". I am using ubuntu and have installed "apache2" and "php5". My CSS file contains the following code:

**main.css**
```
background-color:#00437A;
	background-image:url("../images/black-blue-grad2.png");
	background-repeat:repeat-x;
	background-attachment:fixed;
	background-position:top;
```

"index.php" and "style.php" are both in the "/" root directory, and the "menu.css" file is in "/css". The image is in "/images/"

Remember, all of my other CSS renders perfect. 

I tried uploading everything to my dreamhost server with no success. This makes me think it is not a problem with my php server, I am assuming they have set things up correctly. 

Additionally, after troubleshooting for a while with no success I made a copy of my "index.php" file and named it "index.html". I then removed all includes and replaced them with the included files text. Because everything was just HTML and CSS I was then able to simply open the "index.html" file in my browser. Sure enough, my background-image displayed perfectly, tiled in the horizontal direction. 

Any help is appreciated!

---

### Post by Smart Viking on 2011-05-29
Open index.php in your browser, then copy the page source from View->Page Source in here

---

### Post by lavinog on 2011-05-29
> **bcn17 said:**
> 
**main.css**
```
background-color:#00437A;
	background-image:url("../images/black-blue-grad2.png");
	background-repeat:repeat-x;
	background-attachment:fixed;
	background-position:top;
```

"index.php" and "style.php" are both in the "/" root directory, and the "menu.css" file is in "/css". The image is in "/images/"

Have you tried using the current folder instead of the parent:
```

background-image:url("./images/black-blue-grad2.png");

```

Also it helps to look at the apache error logs.  You might see something like "File not found...blah"

---

### Post by bcn17 on 2011-05-29
> **Smart Viking said:**
> Open index.php in your browser, then copy the page source from View->Page Source in here

After pointing browser to "localhost" and then viewing the page source, this is my code:
```

<!DOCTYPE html> 
<html> 
<head> 
	<meta charset="utf-8" /> 
 
	<title> Space</title> 
	
	<link rel="stylesheet" type="text/css" href="css/reset.css" /> 
<link rel="stylesheet" type="text/css" href="css/main.css" /> 
<link rel="icon" type="image/png" href="images/blue.png" /> 
  
<!-- 	<link rel="stylesheet" type="text/css" href="css/reset.css" />
	<link rel="stylesheet" type="text/css" href="css/main.css" />
	<link rel="icon" type="image/png" href="images/blue.png" />	!--> 
 
	
</head> 
<body> 
 
<header> 
	<h1>Space</h1> 
</header> 
 
	<nav> 
	<ul> 
	<li><a href="">.com</a></li>		
	<li><a href="">about</a></li> 
	<li><a href="">computers</a></li> 
	<li><a href="">archives</a></li> 
	<li><a href="">contact</a></li> 
</ul> 
 
 
	</nav>	
 
	<section> 
		
	</section> 
	
	<article> 
			<h1>Test header</h1> 
				<p>From </p> 
 
<h1>Something</h1> 
				<p>This </p> 
<h1>Awesomeness!!</h1> 
				<p>Mounting </p> 
 
 
	</article> 
	
	<footer> 
		<p>Creative Commons license.</p> 
	</footer> 
</body> 
</html> 
```

This is the contents of the reset.css file:
```
/* 
html5doctor.com Reset Stylesheet
v1.6.1
Last Updated: 2010-09-17
Author: Richard Clark - http://richclarkdesign.com 
Twitter: @rich_clark
*/

html, body, div, span, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
abbr, address, cite, code,
del, dfn, em, img, ins, kbd, q, samp,
small, strong, sub, sup, var,
b, i,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section, summary,
time, mark, audio, video {
    margin:0;
    padding:0;
    border:0;
    outline:0;
    font-size:100%;
    vertical-align:baseline;
    background:transparent;
}

body {
    line-height:1;
}

article,aside,details,figcaption,figure,
footer,header,hgroup,menu,nav,section { 
	display:block;
}

nav ul {
    list-style:none;
}

blockquote, q {
    quotes:none;
}

blockquote:before, blockquote:after,
q:before, q:after {
    content:'';
    content:none;
}

a {
    margin:0;
    padding:0;
    font-size:100%;
    vertical-align:baseline;
    background:transparent;
}

/* change colours to suit your needs */
ins {
    background-color:#ff9;
    color:#000;
    text-decoration:none;
}

/* change colours to suit your needs */
mark {
    background-color:#ff9;
    color:#000; 
    font-style:italic;
    font-weight:bold;
}

del {
    text-decoration: line-through;
}

abbr[title], dfn[title] {
    border-bottom:1px dotted;
    cursor:help;
}

table {
    border-collapse:collapse;
    border-spacing:0;
}

/* change border colour to suit your needs */
hr {
    display:block;
    height:1px;
    border:0;   
    border-top:1px solid #cccccc;
    margin:1em 0;
    padding:0;
}

input, select {
    vertical-align:middle;
}
```

This is the contents of the main.css file:
```


* {border:solid;}

html {

}

body {
	
	margin:35px 35px 70px 35px;
		background-color:#00437A;
	background-image:url("../images/black-blue-grad2.png"); /*Why is this image not printing?*/
	background-repeat:repeat-x;
	background-attachment:fixed;
	background-position:top;
	
	
		

	
}
header {	
	margin:0px 0px 0px 90px;
	width:350px;
	background-color:rgba(255,255,255,1);
	outline-color:rgba(212,146,168,1);
	outline-style:solid;
	outline-width:25px;
	text-align:center;
	border:solid;	
}
header > h1{
	font-size:2em;
	padding:5px;	
}
nav {
	width:200px;
	margin-top:85px;
	margin-left:100px;
	background-color:rgba(212,146,168,1);
	outline-color:rgba(212,146,168,1);
	outline-style:solid;
	outline-width:40px;
	float:left;	
}

nav ul {
	margin:70px 0px 35px 0px;
	text-align:center;

}

nav ul li{
	/*display:inline;*/
	padding:.5em;
	border:solid;
	margin:10px;
	background-color:rgba(255,255,255,1);
}

article {
	background-color:rgba(248,236,210,1);
	margin-left:200px;
	padding:70px 15px 60px 170px;
	min-height:650px;

}

article > h1 {
	background-color:rgba(255,255,255,1);
	font-size:1.7em;
	margin:0px 0px 0px 0px;
	padding:10px 5px 10px 5px;
	
}
/*
article > h1 > p {	WTF!!! why is this selector not working
	background-color:rgba(255,255,255,1);
	font-size:1em;
	margin:0px 0px 0px 0px;
	padding:0px 5px 0px 5px;
}

*/


footer {
	background-color:rgba(212,146,168,1);
	text-align:center;
	margin-left:100px;
	margin-right:65px;
	outline-color:rgba(212,146,168,1);
	outline-style:solid;
	outline-width:40px;
}
```

---

### Post by bcn17 on 2011-05-29
> **lavinog said:**
> Have you tried using the current folder instead of the parent:
```

background-image:url("./images/black-blue-grad2.png");

```

Also it helps to look at the apache error logs.  You might see something like "File not found...blah"

```
tail -f /var/log/apache2/error.log
```

[Sun May 29 02:23:41 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /var/www/images/black-blue-grad2.png, referer: [http://localhost/](http://localhost/)


Thank you!!!!!

---

### Post by szabouk on 2011-05-29
hey;

could you pls try in the browser:

[http://localhost/images/black-blue-grad2.png](http://localhost/images/black-blue-grad2.png)

and lemme know if the bg was there

best
z

---

### Post by bcn17 on 2011-05-29
> **szabouk said:**
> hey;

could you pls try in the browser:

[http://localhost/images/black-blue-grad2.png](http://localhost/images/black-blue-grad2.png)

and lemme know if the bg was there

best
z

Hey, I just changed the permissions back to see if your "probe" would have helped fix the problem. And it would have worked great. Here is the output to your suggestion:
----------------------------------------------------------------
Forbidden

You don't have permission to access /images/black-blue-grad2.png on this server.
-----------------------------------------------------------------

Thanks for the help everyone...

I feel kinda stupid for this one, but I guess it is pretty easy to do...

My permission were set at 700 on the image.

---

### Post by szabouk on 2011-05-29
> **bcn17 said:**
> Hey, I just changed the permissions back to see if your "probe" would have helped fix the problem. And it would have worked great. Here is the output to your suggestion:
----------------------------------------------------------------
Forbidden

You don't have permission to access /images/black-blue-grad2.png on this server.
-----------------------------------------------------------------

Thanks for the help everyone...

I feel kinda stupid for this one, but I guess it is pretty easy to do...

My permission were set at 700 on the image.

gr8stuff!
...don't mention it ;)

---


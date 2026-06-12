---
title: "CSS question: how to have fixed header and footer images that scroll with the page"
date: 2009-01-23
forum: Programming Talk
---

### Post by AFarris01 on 2009-01-23
Basically what i'm trying to do is this:

I've got a web page, and i'm trying to make the body of the page look like a piece of paper, with the top and bottom edges 'curled' a little using only HTML and CSS.  I've been attempting to accomplish this by having a thin textured background image that repeats in the y dir to make up the actual 'paper' and 2 separate images, one fixed at the top  just before the 'paper' and one at the bottom of the page right after the 'paper' to make the 'curls' so the whole page looks like one continuous sheet no matter how long it is.

I've almost got it working... but almost is the key word.  The bottom curly bit works exactly as i want it to... it sits right after the end of the 'paper' picture no matter the length of the body, however i can't seem to get the top to display properly no matter what i try.

what happens is the top curl appears on top of the paper backing, instead of before it, so on the page you can see the paper behind the curl.  this is incredibly frustrating, because I can't figure out how to make it work right... so i was hoping some awesome person here could help me out :)  heres my CSS sheet:

```

/******* Standard Style Elements *******/
html {
	background: black url('backdrop.jpg') repeat fixed center;
	margin-left: 0%;
	margin-right: 0%;
	}
body { 
	width: 930px;
	background: transparent url('paperback-thin.png') repeat-y scroll center;
	color: black;
	margin-top: -8px;
	margin-bottom: -8px;
	margin-left: auto;
	margin-right: auto;
	}

	
/******* DIV CLASSES *******/

#topper {
	position: absolute;
	width: 930px;
	height: 80px;
	padding-bottom: 10px;
	padding-top: 10px;
	background: transparent url('topper.png') no-repeat scroll top;
	position: center;
	}
	
#trailer {
	position: absolute;
	width: 930px;
	height: 79px;
	background: transparent url('trailer.png') no-repeat scroll bottom;
	position: center;
	}


```

and my HTML page:

```

<html>

<head>
<link rel="SHORTCUT ICON" href="favicon.ico">

<title>TITLE GOES HERE
</title>
<link rel="stylesheet" type="text/css" href="main_stylesheet.css" />
</head>
	
<body>
	<div id="topper"></div>
		<br>
		content content content...
		<br>
	<div id="trailer"></div>
</body>

</html>

```

any help is greatly appreciated!:D

---

### Post by AFarris01 on 2009-01-23
I just figured out what i was doing wrong... 

Basically the problem was that i should've been defining the page background in a new container, rather than trying to keep it in the 'body' declare.  I had tried this before, but it didnt work, because i was tryign to turn the new 'container' into the body as well... heres how i got it workin...

removed the background declare from the 'body' area in the CSS, and added this to the end of the file:
```

#container {
	background: transparent url('paperback-thin.png') repeat-y scroll center;
	}

```

Then modified the HTML to look like this:

```

<html>

<head>
<link rel="SHORTCUT ICON" href="favicon.ico">

<title>TITLE GOES HERE
</title>
<link rel="stylesheet" type="text/css" href="main_stylesheet.css" />
</head>
	
<body>
	<div id="topper"></div>
	<div id="container">
		<br>
		content content content...
		<br>
	</div>
	<div id="trailer"></div>
</body>

</html>

```

and thats it! worked perfectly

---


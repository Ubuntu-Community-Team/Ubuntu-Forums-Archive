---
title: "[css] positioning images from sliced template"
date: 2008-12-18
forum: Programming Talk
---

### Post by TreeFinger on 2008-12-18
what is the best approach when positioning images that have been sliced out of a template?

BTW, I think the template was not sliced in the perfect way...

the layout is pretty much a square around the 'content' of the page, which will be plain text for the most part, and some images.

---

### Post by TreeFinger on 2008-12-18
yea, I am replying to my own post.

Currently, I have one large div container inside the body, and then a div container around the banner, the xhtml image inside that container, the left side container and the left side image inside.

here is my css:

[php]
body {
	display : block ;
	background-color : #D2B48C ;
	text-align : center ;	
	margin-top : 10px ;
	margin-left : 10px ;
}

#container {
	display : inline ;
	text-align : left ;
	width : 100% ;
	height : 100% ;
	display : inline ;

}

#banner_container {
	display : inline ;
	width : 917px ;
	height : 170px ;
}

img.top_banner {
	width : 100% ;
	height : 100% ;
}

#leftside_container {
	display : inline ;
	position : fixed ;
	left : 0px ;
	top : 193px ;
	width : 109px ;
	height : 527px ;
}

img.leftside {
	width : 100% ;
	height : 100% ;
}
[/php]

the xhtml validates under strict. i have not uploaded to the web yet so I can not yet validate the css in any way that I am aware of. Showing up just dandy in firefox, but not lining up in IE. What can I do?

---

### Post by TreeFinger on 2008-12-18
Why does IE mess things up???? Looks PERFECT in firefox... there is a gap. it is like [php]display : inline ;[/php]is having no affect on the document in IE...

---

### Post by kostkon on 2008-12-18
> **TreeFinger said:**
> Why does IE mess things up???? Looks PERFECT in firefox... there is a gap. it is like [php]display : inline ;[/php]is having no affect on the document in IE...
Try removing the 
```
text-align: center
```
from the body element since this makes IE to try to center all of the elements in the page (crazy, I know...) and put it only where it is needed.

---

### Post by TreeFinger on 2008-12-18
> **kostkon said:**
> Try removing the 
```
text-align: center
```
from the body element since this makes IE to try to center all of the elements in the page (crazy, I know...) and put it only where it is needed.

that did something ;p

the reason I had that there was because I would like the layout centered... should I text-align center in the body and then text-align left in the container?

---

### Post by kostkon on 2008-12-18
> **TreeFinger said:**
> that did something ;p

the reason I had that there was because I would like the layout centered... should I text-align center in the body and then text-align left in the container?
You could try that, yes, although I am not sure what bad things may cause :rolleyes:

---

### Post by TreeFinger on 2008-12-18
> **kostkon said:**
> You could try that, yes, although I am not sure what bad things may cause :rolleyes:

somehow.. i got it working....


now hopefully i can get the right and bottom parts working correctly also .. thank you for the help.

---

### Post by kostkon on 2008-12-19
Just a tip:

  You could also use an image replacement technique of your choice for the banner and wrap the text of the banner, I assume the name of the site, around a H1 tag. This will make the page/site more semantic and more discoverable by search engines

---

### Post by TreeFinger on 2008-12-19
I have hit a wall. I can not show this image that must be displayed behind the navigation menu to show up.. the content must be over the background image...

i am sharing everything now.. been trying everything for an hour or so...

xhtml:
[php]
<?xml version="1.0" encoding="iso-8859-1"?>

<!-- 'About' Page -->

<!DOCTYPE html 
     PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
     "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" lang="EN">

<head>
<link rel="stylesheet" type="text/css" href="styles.css" />
<title>Professor Fountain's Cabinet of Wonder -- About</title>
<!-- Need to add Meta Tags -->
</head>

<body>
	<div id="background_image">
	<div id="container">

		<!-- Lets try setting up the left side of the page first. The way this is sliced will most likely mean the entire top banner will also need to be set up first. -->

		<!-- Here is the Banner -->
		<div id="banner_container">
			<img class="top_banner" src="images/index_01.gif" alt="Professor Fountain's Cabinet of Wonder - Top Banner" />
		</div>
		<!-- Next is the left part of the page... -->
		<div id="leftside_container">
			<img id="leftside" src="images/index_02.gif" alt="Cabinet of Wonder - Left Side" />
		</div>

		<!-- Next is the content area...-->
		<div id="content_container">
			

		</div>
		<!-- END OF CONTENT AREA -->

<!--
		<!-- Next is the Navigation Bar -->
		<div id="nav_container">
		<ul>
			<li class="nav_item"><a href="about.html"><img class="nav_item" src="images/working_03.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="history.html"><img class="nav_item" src="images/working_04.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="performances.html"><img class="nav_item" src="images/working_05.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="contact.html"><img class="nav_item" src="images/working_06.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="links.html"><img class="nav_item" src="images/working_07.gif" alt="Main Navigation - About" /></a></li>
			</ul>
		</div>
		<!-- END OF NAV BAR -->

		<!-- HERE IS THE IMPORTANT (YOU EDIT THIS) CONTENT -->
		<!-- Center Text Box --> -->
	</div>	
	</div>

</body>
</html>
[/php]

css:
[php]
<?xml version="1.0" encoding="iso-8859-1"?>

<!-- 'About' Page -->

<!DOCTYPE html 
     PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
     "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" lang="EN">

<head>
<link rel="stylesheet" type="text/css" href="styles.css" />
<title>Professor Fountain's Cabinet of Wonder -- About</title>
<!-- Need to add Meta Tags -->
</head>

<body>
	<div id="background_image">
	<div id="container">

		<!-- Lets try setting up the left side of the page first. The way this is sliced will most likely mean the entire top banner will also need to be set up first. -->

		<!-- Here is the Banner -->
		<div id="banner_container">
			<img class="top_banner" src="images/index_01.gif" alt="Professor Fountain's Cabinet of Wonder - Top Banner" />
		</div>
		<!-- Next is the left part of the page... -->
		<div id="leftside_container">
			<img id="leftside" src="images/index_02.gif" alt="Cabinet of Wonder - Left Side" />
		</div>

		<!-- Next is the content area...-->
		<div id="content_container">
			

		</div>
		<!-- END OF CONTENT AREA -->

<!--
		<!-- Next is the Navigation Bar -->
		<div id="nav_container">
		<ul>
			<li class="nav_item"><a href="about.html"><img class="nav_item" src="images/working_03.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="history.html"><img class="nav_item" src="images/working_04.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="performances.html"><img class="nav_item" src="images/working_05.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="contact.html"><img class="nav_item" src="images/working_06.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="links.html"><img class="nav_item" src="images/working_07.gif" alt="Main Navigation - About" /></a></li>
			</ul>
		</div>
		<!-- END OF NAV BAR -->

		<!-- HERE IS THE IMPORTANT (YOU EDIT THIS) CONTENT -->
		<!-- Center Text Box --> -->
	</div>	
	</div>

</body>
</html>
[/php]

---

### Post by mike_g on 2008-12-19
You can use the [Z-Index](http://www.w3schools.com/Css/pr_pos_z-index.asp) propery to set what elements go ontop of what. You will need to use relative or absolute positioning on the elements for it to work tho.

---

### Post by TreeFinger on 2008-12-19
I have been working at this non-stop. Thank you for any replies!

I am so close.. yet so far...

[IMG]http://i40.tinypic.com/fav1mw.jpg[/IMG]

---

### Post by TreeFinger on 2008-12-19
and my current code...

xhtml:
[php]
<?xml version="1.0" encoding="iso-8859-1"?>

<!-- 'About' Page -->

<!DOCTYPE html 
     PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
     "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" lang="EN">

<head>
<link rel="stylesheet" type="text/css" href="styles.css" />
<title>Professor Fountain's Cabinet of Wonder -- About</title>
<!-- Need to add Meta Tags -->
</head>

<body>
		<div id="container">

		<!-- Lets try setting up the left side of the page first. The way this is sliced will most likely mean the entire top banner will also need to be set up first. -->

		
		
		
		
		<!-- Here is the Banner -->
		<div id="banner_container">
			<img class="top_banner" src="images/index_01.gif" alt="Professor Fountain's Cabinet of Wonder - Top Banner" />
		</div>





		<!-- Next is the left part of the page... -->
		<div id="leftside_container">
			<img id="leftside" src="images/index_02.gif" alt="Cabinet of Wonder - Left Side" />
		</div>






		<!-- Next is the Navigation Bar -->
		<div id="nav_container">
			<img id="nav_bg_image" src="images/index_02.gif" alt="Cabinet of Wonder - Left Side" />
		<ul>
			<li class="nav_item"><a href="about.html"><img class="nav_item" src="images/working_03.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="history.html"><img class="nav_item" src="images/working_04.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="performances.html"><img class="nav_item" src="images/working_05.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="contact.html"><img class="nav_item" src="images/working_06.gif" alt="Main Navigation - About" /></a></li>
			<li class="nav_item"><a href="links.html"><img class="nav_item" src="images/working_07.gif" alt="Main Navigation - About" /></a></li>
			</ul>
		</div>
		<!-- END OF NAV BAR -->



		<!-- Next is the right part of the page... -->
		<div id="rightside_container">
			<img id="rightside" src="images/index_08.gif" alt="Cabinet of Wonder - Left Side" />
		</div>
		<!-- END OF RIGHT PART OF PAGE -->



		<!-- Background of cabinet -->
		<img class="bg_image" src="images/index_09.gif" alt="The background of Professor Fountain's Cabinet" />


	</div>

</body>
</html>
[/php]


css:
[php]
body {
	z-index : -2 ;
	display : block ;
	background-color : #D2B48C ;
	margin-top : 10px ;
	margin-left : 10px ;
	width : 99% ;
}

h1.content_heading {
}

	#container {
		display : inline ;
		margin-top : 0px ;
		margin-left : 0px ;
		width : 917px ;
		height : 697px ;
		position : relative ;
		left : 10px ;
		top : 10px ;
	}

		img.bg_image {
			z-index : -1 ;
			display : inline ;
			position : relative ;
			top : -481px ;
			left : 119px ;
			width : 710px ;
			height : 481px ;
		}

		#banner_container {
			display : inline ;
			height : 220px ;
			width : 99% ;
			position : relative ;
			top : 10px ;
			left : 10px ;
		}

			img.top_banner {
				display : inline ;
				height : 220px ;
				width : 917px ;
			}

		#leftside_container {
			display : inline ;
			position : relative ;
			left : 10px ;
			top : 4px ;
			width : 109px ;
			}

			img.leftside {
				display : inline ;
				width : 109px ;
				height : 550px ;
			}
			
		#nav_container {
			display : inline ;
			position : relative ;
			left : -35px ;
			top : -477px ;
			height : 48px ;
			width : 695px ;
		}

			div#nav_container ul {
				display : inline ;
				white-space : nowrap ;	
			}

			div#nav_container li.nav_item {
				display : inline ;
				width : auto ;
				list-style-type : none;
				
			}

			div#nav_container img.nav_item {
				display : inline ;
				border : medium ;
			}

			#rightside_container {
				display : inline ;
				position : relative ;
				left : 10px ;
				top : 4px ;
			}

			img.rightside {
				display : inline ;
				width : 109px ;
				height : 550px ;
			}

			img.nav_bg_image {
				display : inline ;
			}
[/php]

---

### Post by TreeFinger on 2008-12-19
dang, when I change resolutions things are really messed up. I need some serious advice !

---


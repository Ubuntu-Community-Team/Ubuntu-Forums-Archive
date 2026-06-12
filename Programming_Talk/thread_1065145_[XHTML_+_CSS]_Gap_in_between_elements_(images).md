---
title: "[XHTML + CSS] Gap in between elements (images)"
date: 2009-02-09
forum: Programming Talk
---

### Post by TreeFinger on 2009-02-09
[www.personal.psu.edu/sjc5002/pf](www.personal.psu.edu/sjc5002/pf)

anyone recommend ways to get rid of that gap between the 2 side pieces and the top image?

(i didn't design this site.)

---

### Post by JimBuntu on 2009-02-09
have you tried: padding: 0; margin: 0; in your .css file for each of the columns?

I am dealing with a similar problem with a page that I am writing. I cant figure out how to take all of the space out from between the heading, body and footer.

---

### Post by Reiger on 2009-02-09
Not to forget parent elements!

---

### Post by TreeFinger on 2009-02-09
> **Reiger said:**
> Not to forget parent elements!

is this easily fixex? and you are just leading me on? ;p

I'l try until Friday, but that is when it is due! wish me luck.

---

### Post by Peter76 on 2009-02-10
From your CSS file:

```
* {
  background-color:#D2B48C;	/* MAIN css for professor fountain */
  margin:0px 0px 0px 0px;
}

body {
  display:block;
}
```

Change to :

```
* {
  margin: 0;
  padding: 0;
}

img {
  border: none;
}

body { 
  background-color: #D2B48C;
}
```

This will set the margin and padding of all elements to zero. You can delete later settings of these later on now. This will also make sure no border is displayed around images.
I also put the background-color setting in the body specific part and not the general( * ) part, because I guess you just want to set the background on the body and not on any element.
I als left out the display: block; setting on the body; the body already is a block level element ( AFAIK ) Can somebody tell me if I'm wrong here?
Hope this helps...

Good Luck, Peter

---

### Post by TreeFinger on 2009-02-10
well, I did what you suggested. I put padding:0, margin:0, border:none for every element. my css file now looks like this:

[php]
* {
background-color:#D2B48C;	/* MAIN css for professor fountain */
}
body {
background-color:#D2B48C;
margin:0;
padding:0;
}
div#ROOT {
margin:0;
padding:0;
width:975px;
margin-left:auto;
margin-right:auto;
text-align:center;
position:relative;
border:none;
}
img#top-banner {
margin:0;
padding:0;
width:564px;
height:128px;
margin-left:auto;
margin-right:auto;
border:none;
}
img#top-nav {
margin:0;
padding:0;
width:991px;
height:92px;
border:none;
}

div#div-navigation {
width:789px;
margin:0;
padding:0;
border:none;
/* background: */
}
ul#ul-navigation {
margin:0;
padding:0;
list-style-type:none;
border:none;
}

li.nav-link {
margin:0;
padding:0;
float:left;
width:17%;
border:none;
}

div#main-content {
min-height:594px;
width:100%;
margin:0;
padding:0;
border:none;
}
	/* div#left-column {
	width:93px;
	min-height:594px;
	float:left;
	} */
img#left-column {
margin:0;
padding:0;
float:left;
border:none;
}
	/* div#mid-column {
	min-height:594px;
	width 500px;
	} */
	/* div#right-column {
	width:93px;
	min-height:594px;
	
	} */
img#right-column {
float:right;
margin:0;
padding:0;
border:none;
}

img#bot-banner {
margin:0;
padding:0;
width:564px;
height:128px;
display:block;
margin-left:auto;
margin-right:auto;
border:none;
}
[/php]

---

### Post by TreeFinger on 2009-02-10
also changed the xhtml.

getting better :)
[php]
<!DOCTYPE htmlPUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 

<html xmlns="http://www.w3.org/1999/xhtml" lang="EN"> 
 
<head> 
<link rel="stylesheet" type="text/css" href="pf-style.css" /> 
<title>Professor Fountain's Cabinet</title> 
</head> 

<!-- TRYING TO USE THE FOLLOWING SYSTEM.. 'PARENT ELEMENT'-'CHILD ELEMENT'-->
<!-- FROM WHAT I HAVE LEARNED IN THE PAST 1 DAY IS THAT THE LESS DIV ELEMENTS THE BETTER. -->
<body>
	<div id="ROOT">


		<!-- TOP BANNER YOOOOOOO -->
		<img id="top-banner" src="images/top-banner.gif" alt="Professor Fountain's Top Banner" />

		<!-- that little piece of wood yooooooo -->
		<img id="top-nav" src="images/nav-container.gif" alt="professor fountain stupid image" />

		<img id="left-column" src="images/left-col.gif" alt="left column image" />

		<img id="right-column" src="images/right-col.gif" alt="right column image" />

		<div id="div-navigation">
		<!-- ul#navigation -->
		<ul id="ul-navigation">
			<li class="nav-link"><a href="index.html">Home</a></li>
			<li class="nav-link"><a href="history.html">History</a></li>
			<li class="nav-link"><a href="perf.html">Performances</a></li>
			<li class="nav-link"><a href="contact.html">Contact</a></li>
			<li class="nav-link"><a href="contact.html">Links</a></li>
		</ul> <!-- closing navigation-->
		</div>
		<!-- END NAVIGATTION, OVER AND OUT -->

		<h1>Welcome</h1>

		
		
		<img id="bot-banner" src="images/bot-banner.gif" alt="professor fountain bottom image" />

	<!-- THE END -->
	</div>
</body>
</html>
[/php]

---

### Post by TreeFinger on 2009-02-10
thank you fellows very much. marking as solved :)

---


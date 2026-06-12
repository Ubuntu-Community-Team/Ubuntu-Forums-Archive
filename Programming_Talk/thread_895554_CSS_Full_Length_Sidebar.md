---
title: "CSS Full Length Sidebar?"
date: 2008-08-20
forum: Programming Talk
---

### Post by Arctic_Fox on 2008-08-20
Hey, I have a pretty simple question. I'm trying to make a sidebar to the main content in a page where the sidebar extends through the entire content area. What I have (simplified) is:

html, body {height: 100%; width: 100%;}

#container {
	margin-left: auto; 
	margin-right: auto;
	height: 100%;
	width: 83%;
        background: #ffffff
}
.sbar_right {
		float: right;
		background: #aaaaaa
		min-height: 100%
}

Then in the HTML:

<html><head>
	<title>page</title><style type="text/css">
	</style></head>
	<body>
	<div id = "container">
		 <div class = "sbar_right" style = "width:17%; height:100%">
                  bla bla stuff
                 </div>
                 <div name = "content" style = "width: 87%">
                 al;sdfkjalsdkfj
                 </div>
                 <div style = "clear: both;"></div>
        </div>
        </body>
</html>

I'm using firefox, and the sidebar only extends the length of the screen (the content is longer than the screen). Thanks for the Help!

---

### Post by mike_g on 2008-08-20
One possible way to do it would be to give your sidebar and content an id add size them when your page loads with javascript. Like this IIRC:
```
function SetHeight()
{
	s = document.getElementById('sidebar');
	c = document.getElementById('content');

	if(s.offsetHeight < c.offsetHeight)
	{
		s.style.height = c.offsetHeight+"px";
	}
	else
	{
		c.style.height = s.offsetHeight+"px";
	} 
}

....

<body onload="SetHeight()">

</body>
```

Edit; If you really want to do it in CSS then you will have to fake the appearance of having a sidebar aligned with the main content. can be done by adding a container that goes around both divs and has the background for both the sidebar and the conatiner.

---

### Post by Arctic_Fox on 2008-08-20
Thanks! that worked.

---


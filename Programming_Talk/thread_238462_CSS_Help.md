---
title: "CSS Help"
date: 2006-08-17
forum: Programming Talk
---

### Post by stormblue on 2006-08-17
You can view the HTML and CSS [here]("http://blowback.zapto.org/metromusic/")
```

<style type="text/css">
		html {
			background: #CACCB4;
		}
		body {
		font: 16px arial, sans-serif; }
		

		#sidebar-a {
			float: right;
			width: 250px;
			margin: 0;
			margin-left: ;
			padding: 5px;
			background-color: #FFF000;
			border: 2px solid black;
			position: relative;
		}
		
	
	}
	
	pre {text-indent: 30px}

	#tabmenu {
		color: #000;
		margin: 12px 0px 0px 0px;
		z-index: 1;
		padding-left: 10px 
		}

	#tabmenu li {
		display: inline;
		overflow: hidden;
		list-style-type: none; }

	#tabmenu a, a.active {
		color: #DEDECF;
		background: #898B5E;
		font: bold 1em "Trebuchet MS", Arial, sans-serif;
		border: 2px solid black;
		padding: 2px 5px 0px 5px;
		margin: 0px;
		text-decoration: none; }

	#tabmenu a.active {
		background: #ABAD85;
		border-bottom: 3px solid #ABAD85; }

	#tabmenu a:hover {
		color: #fff;
		background: #ADC09F; }

	#tabmenu a:visited {
		color: #E8E9BE; }

	#tabmenu a.active:hover {
		background: #ABAD85;
		color: #DEDECF; }

	#left {
		font: 0.9em/1.3em "bitstream vera sans", verdana, sans-serif;
		text-align: justify;
		background: #FFF000;
		padding: 20px;
		border: 2px solid black;
		border-top: 2px solid black;
		width: 50%;
		z-index: 2;
		float: left;
		position: absolute;
			}

	#left a {
		text-decoration: none;
		color: #E8E9BE; }

	#left a:hover { background: #898B5E; }
	</style>
```


```
<body>
<ul id="tabmenu">
	<li><a href="tab1.html">Home</a></li>

	<li><a href="tab2.html">Bands</a></li>
	<li><a class="active" href="tab3.html">Metros</a></li>
</ul>

<div id="left">
  <p>Content 1 </p>
  </div>
<div id="sidebar-a">right side</div>



</body>
```

I want the left side to be fluid and the right side to be fixed.  I want the right side to be a fixed distance from the left hand side, and never go behind it, but as the window is expanded the left collumn will expand.

Any help or suggestions?

Thanks!

---

### Post by VTStevenVT on 2006-08-18
Alright i think i know what you want here so here is the solution. whats happening is that when you float the right sidebar to the right it will always be measured relative to the right side of the window, but because you want it to be a fixed distance from the content, the answer is to float it to the left and give the content a right-margin. Also you have to set the z-indexes to the same so the content's new right-margin will push the right bar to the right and so the contents wont overlap each other..

The reason this fix works is because left floating is set up like a flow control. The first thing that is floated to the left is put where it goes, the next thing will then be put the right of the first or on a new line if there isn't enough room. With my fix here, if you shrink the window too small the right bar will be put on the next line, but this is because of the way float flow works. But there is a ton of formatting issues when the window is shrunk too small. For a nice visual look at this:
[http://css.maxdesign.com.au/floatutorial/introduction13.htm]("http://css.maxdesign.com.au/floatutorial/introduction13.htm")

For more Css Float help try going through the tutorials here:
[http://css.maxdesign.com.au/floatutorial/]("http://css.maxdesign.com.au/floatutorial/")

Anyway here is the new Css Code, the html can stay the same:

```

<style type="text/css">
html {
	background: #CACCB4;
}
body {
	font: 16px arial, sans-serif; 
}
		

#sidebar-a {
	float: left;
	width: 250px;
        /* I tried putting a left-margin on the right bar
           but that didn't work so see below in #left where i put a right
           margin on the left content */
	/*margin: 0px 0px 100px 0px;*/
	padding: 5px;
	background-color: #FFF000;
	border: 2px solid black;
	position: relative;
	z-index: 2;
}
		
pre {
	text-indent: 30px;
}

	#tabmenu {
		color: #000;
		margin: 12px 0px 0px 0px;
		z-index: 1;
		padding-left: 10px 
		}

	#tabmenu li {
		display: inline;
		overflow: hidden;
		list-style-type: none; }

	#tabmenu a, a.active {
		color: #DEDECF;
		background: #898B5E;
		font: bold 1em "Trebuchet MS", Arial, sans-serif;
		border: 2px solid black;
		padding: 2px 5px 0px 5px;
		margin: 0px;
		text-decoration: none; }

	#tabmenu a.active {
		background: #ABAD85;
		border-bottom: 3px solid #ABAD85; }

	#tabmenu a:hover {
		color: #fff;
		background: #ADC09F; }

	#tabmenu a:visited {
		color: #E8E9BE; }

	#tabmenu a.active:hover {
		background: #ABAD85;
		color: #DEDECF; }

	#left {
		font: 0.9em/1.3em "bitstream vera sans", verdana, sans-serif;
		text-align: justify;
		background: #FFF000;
		padding: 20px;
		border: 2px solid black;
		border-top: 2px solid black;
		z-index: 2;
		float: left;
		width: 50%;
		margin: 0px 100px 0px 0px;
			}

	#left a {
		text-decoration: none;
		color: #E8E9BE; }

	#left a:hover { background: #898B5E; }
	</style>

```

Now i picked a few arbitrary margins which you  can change to fit your needs.

Let me know if you need more help.

-Steve

---

### Post by stormblue on 2006-08-18
Thanks for the help.  I'll let you know if I run into any other problems.

---

### Post by stormblue on 2006-08-19
Using your CSS I was able to create [this]("http://blowback.zapto.org/metromusic/")which is closer.  What I want now is content to expand and content 1 as a window is resized, but I want the ride side column to be equal distant from the right side as the left side is.  I'm not sure if this is very clear, but the content would be fluid and the side bar would be static.

Thanks for the help so far.

---

### Post by stormblue on 2006-08-20
I've been doing a bit of research and I found [this]("http://www.bluerobot.com/web/layouts/layout2.html") with the CSS [here]("http://www.bluerobot.com/web/layouts/view_css.asp?layout=layout2")

Is that the way to do the right column, with the absolute, or is there a better way?  I've read somewhere that absolute positioning was to be avoided when possible, but anyone have any suggestions.  Thanks!

---

### Post by VTStevenVT on 2006-08-21
Alright I played with this a bit this weekend, but was only able to make it work when the right menu was fluid, not fixed like you want. I looked at that example you linked, and I hadn't of thought of doing it that way but it looks good and if I where you I'd try it out and test it on a few different browsers, and if it looks ok then your good. Otherwise, if your feeling really ambitious run it through w3c. But personally I think if you hit the major browers ( Firefox, IE6, Opera, Safari, etc.. ) then if a off-the-wall browser hits your page, you can put a disclaimer about "this page requires .... " to be displayed correctly.

Good researching on finding that example.

-Steve

---

### Post by VTStevenVT on 2006-08-21
Ok i was thinking about this today for a second and then it dawned on me.... use the concept of padding the body to accomplish this task. I was working on a peice of code from the Holy Grail CSS idea, which is 3 columns a header/footer and no confusing html divs and any of the 3 columns can be the longest and the footer will clear them all, the code for this can be seen here:

[http://www.alistapart.com/d/holygrail/example_4.html]("http://www.alistapart.com/d/holygrail/example_4.html")

But anyway, here is what I have now, and I think it works the way you want and it doesn't use absolutes.

```

<style type="text/css">
html {
	background: #CACCB4;
}
body {
	font: 16px arial, sans-serif; 
	padding-right: 224px; /* The key to how this works */
			      /* (SB Width) + (SB Padding * 2) + (SB Border * 2) */
			      /* 200 + 10*2 + 2*2 = 224 */
}
/*Sidebar, refered to as SB */	
#sidebar-a {
	float: left;
	background-color: #FFF000;
	border: 2px solid black;
	position: relative;
	width: 200px;           /* SB width */
	padding: 0 10px;        /* SB padding */
	margin-top: 0px;
	position: relative;
	background: #FFF000;

}
		
pre {
	text-indent: 30px;
}

	#tabmenu {
		color: #000;
		margin: 12px 0px 0px 0px;
		z-index: 1;
		padding-left: 10px 
		}

	#tabmenu li {
		display: inline;
		overflow: hidden;
		list-style-type: none; }

	#tabmenu a, a.active {
		color: #DEDECF;
		background: #898B5E;
		font: bold 1em "Trebuchet MS", Arial, sans-serif;
		border: 2px solid black;
		padding: 2px 5px 0px 5px;
		margin: 0px;
		text-decoration: none; }

	#tabmenu a.active {
		background: #ABAD85;
		border-bottom: 3px solid #ABAD85; }

	#tabmenu a:hover {
		color: #fff;
		background: #ADC09F; }

	#tabmenu a:visited {
		color: #E8E9BE; }

	#tabmenu a.active:hover {
		background: #ABAD85;
		color: #DEDECF; }

	#left {
		font: 0.9em/1.3em "bitstream vera sans", verdana, sans-serif;
		text-align: justify;
		background: #FFF000;
		padding: 20px;
		border: 2px solid black;
		border-top: 2px solid black;
		float: left;
		width: 100%;
		margin-right: 14px; /* Sets how far from the content the SB should be*/
				    /* I chose (((body-padding-right total) - (sidebar width)) / 2) + SB Boarder Width */
	                            /* but it is best to just change it and look at it */
		position: relative;
			}

	#left a {
		text-decoration: none;
		color: #E8E9BE; }

	#left a:hover { background: #898B5E; }

	</style>
	

<body>
<ul id="tabmenu">
	<li><a href="tab1.html">Home</a></li>

	<li><a href="tab2.html">Bands</a></li>
	<li><a class="active" href="tab3.html">Metros</a></li>
</ul>

<div id="left">
  <p>Content 1 </p>
</div>
<div id="sidebar-a">right side</div>



</body>


```


Enjoy
-Steve

---

### Post by stormblue on 2006-08-21
Thanks!

---


---
title: "HTML/CSS Puzzle"
date: 2010-08-05
forum: Programming Talk
---

### Post by Ravenshade on 2010-08-05
Right... I have a website, validated to Strict HTML, UTF-8 and I also got the CSS Validated to a level 3 standard by the w3c. 

Unfortunately, I can't work out where I'm getting the extra space from. 

[<url>](<url>). 

I'm using javaScript to point different browsers to different CSS files, so the browser I'm using for development is <browser&version>, it currents *works* for Firefox and sort of works for IE. I can't actually test it on IE because IE doesn't support linux >.<; Nor does Safari. 

Now on the page, down the right hand side, you'll see a thick black line. (It's the body). Now, I have a div tag that I use as the container for the rest of my website instead of using the body. 

I set up the site so that it reaches 100%, I've tried setting max-widths and min-widths, but to no avail, I just can't seem to get rid of the extra 200px worth of black space. 

I think it might have something to do with some floats I'm using, but i'm not sure. I've tried pretty much every way I can think of to get rid of that 200px worth of space but nothing has worked. 

Anyone want to have a crack at the whip? :popcorn:

[HTML]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
	<head>
		<meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
		<title><sitename></title>
		<script type="text/javascript" src="jscript/cssChange.js"></script>	
		<link rel="SHORTCUT ICON" href="<url>/favicon.ico" />
		<link rel="stylesheet" type="text/css" href="h<url>/css/fonts.css" />
	</head>
	<body>
		<div class="container">
			<div class="aboveDiv">
				<div class="headBanner">
					<div class="<a classname">
						<h1><a header></h1>
					</div>
					<div class="tagline">
						<h2><a tagline></h2>
					</div>
				</div>
				<div class="nav">
					<div class="navBlock">
						<a href="index.html">Home!</a> | No more links!
					</div>
				</div>
			</div>
		
			 <div class="central">
			 	<div class="leftDiv"></div>
			 	<div class="middleDiv">
			 		<br />
			 		<div class="textBlock">
			 			<h3>Greetings </h3>
			 			<p>
			 			Welcome to the <site> site. I hope 
			 			<Blurb>.</p>
			 			<p><b><i>The Administrator</i></b></p>
			 		</div>
			 	</div>
			 	<div class="rightDiv">
			 		<div class="lightTextBlock">
			 			<h4>Announcements</h4>
			 			<p class="announcements"> Website in construction phase</p>
			 		</div>
			 		<div class="badgeContainer">
			 			<a href="http://jigsaw.w3.org/css-validator/check/referer">
    							<img style="border:0;width:88px;height:31px"
       								 src="http://jigsaw.w3.org/css-validator/images/vcss-blue"
        							alt="Valid CSS!" />
						</a>

    						<a href="http://validator.w3.org/check?uri=referer">
    							<img src="http://www.w3.org/Icons/valid-xhtml10"
    								alt="Valid XHTML 1.0 Strict" height="31" width="88" />
    						</a>
    						<p class="testedWith">
    							Tested with Opera 10.60, Firefox 3.0, Midori 0.1, 
    						</p>
  						
					</div>	
			 	</div>
			 </div>
		
			<div class="belowDiv">
				<div class="footDiv">
					<script type="text/javascript" src="jscript/date.js"></script>	
					<script type="text/javascript" src="jscript/detectFirefox.js"></script>
					<script type="text/javascript" src="jscript/detectIE.js"></script>
					<script type="text/javascript" src="jscript/detectOpera.js"></script>		
				</div>
			</div>
		</div>
	</body>
</html>[/HTML]

```
/*MainCSS files*/

body {
	background-color: black;
	
}

div.container {
	position: absolute;
	top: -21px; /* Mysterious gap caused by DocType 					Work Around!*/
	left: 0px;
	height: 100%;
	width: 100%;
	max-height: 1200px;
	min-height: 500px;
	max-width: 1200px;
	min-width: 500px;
	
}

div.aboveDiv {
	position: relative;
	top: 0px;
	left: 0px;
	height: 30%;
	min-height: 100px;
	max-height: 200px;
	width: 100%;
	background-color: green;
	
}
div.headBanner {
	position: relative;
	top: 0px;
	height: 80%;
	min-height: 80px;
	max-height: 170px;
	left: 0px;
	width: 100%;
	background-color:  #83EAC8;
}
div.<div name> {
	position: relative;
	top: 0px;
	height: auto;
	width: auto;
	left: 30px;
}

div.tagline {
	position: relative;
	top: -30px;
	height: auto;
	width: auto;
	left: 120px;
}

div.nav {
	position: relative;
	height: 20%;
	max-height: 40px;
	min-height: 30px;
	left: 0px;
	width: 100%;
	background-color: #599F88;
	
	
}

div.central {
	position: relative;
	top: 0%;
	left: 0px;
	height: 60%;
	min-height: 200px;
	max-height: 800px;
	width: 100%;
	min-width: 400px;
	background-color: #599F88;
}

div.leftDiv {
	position: relative;
	left: 0px;
	top: 0px;
	height: 100%;
	min-height: 300px;
	width: 20%;
	max-width: 200px;
	min-width: 50px;
	background-color: #58D4AB;
	float: left;
	display: inline;
}

div.middleDiv {
	position: relative;
	left: 0%;
	top: 0px;
	height: 100%;
	min-height: 300px;
	width: 60%;
	max-width: 600px;
	min-width: 200px;
	background-color: white;
	display: inline;
	float: left;
	
}

div.textBlock {
	position: relative;
	left: 0px;
	top: 0px;
	height: auto;
	width: auto;
	padding: 10px;
}

div.rightDiv {
	position: relative;
	left: 0%;
	top: 0px;
	height: 100%;
	min-height: 300px;
	width: 20%;
	max-width: 200px;
	min-width: 50px;
	background-color: #58D4AB;
	float: left;
	display: inline;
}

div.lightTextBlock {
	position: relative;
	left: 0px;
	top: 0px;
	height: auto;
	width: auto;
	margin-left: 10px;
	margin-top: 10px;
	margin-right: 5px;
	margin-bottom: 5px;
	padding-left: 5px;
	padding-top: 5px;
	padding-right: 5px;
	padding-bottom: 5px;
	background-color: #9EEAD1;
}

div.badgeContainer {
	position: relative;
	height: auto;
	width: auto;
	left: 0px;
	top: 0px;
	margin-left: 10px;
	margin-top: 0px;
	margin-right: 5px;
	margin-bottom: 5px;


}

div.belowDiv {
	position: relative;
	top: 0px;
	left: 0px;
	height: 5%;
	width: 100%;
	background-color: #599F88;
}

div.footDiv {
	position: relative;
	top: 0px;
	left: 0px;
	padding-left: 5px;
	padding-top: 5px;
	height: auto;
	width: auto;
}
```

---

### Post by Hellkeepa on 2010-08-07
HELLo!

Since you didn't reset all of the margins and paddings, you'll get hit by the different standard values the different browsers have. I recommend adding the following to the top of the CSS file, to fix this issue:
```
* {
    margin: 0;
    paddign: 0;
}
```
After you've done that you will most likely have to define a few paddings and margins where you want to have them, where you previously relied upon the default values for your main browser.
That's why I always start with the above in a CSS file, so that I don't have to go back and recreate all of the wanted whitespace regions. ;-)

Happy codin'!

---


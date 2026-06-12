---
title: "Err...Some CSS help?"
date: 2010-10-30
forum: Programming Talk
---

### Post by skytreader on 2010-10-30
Hi. I know that CSS/HTML isn't even programming but just thought I'd try my luck here, if anyone can help me with my problem.

See I'm trying to create a center box which would contain the contents of my page. It looks fine already:

[IMG]http://www.skytreader.net/images/just_fine.png[/IMG]

Until the need for scrolling comes along...

[IMG]http://www.skytreader.net/images/end_there.png[/IMG]

So, how do I remedy that? I want the box to encompass the text till it ends. Or, more specifically, have the box going straight from top to bottom with no margins so that the whole "background" of my page will look as though divided into three: one black box on the leftmost, the big gray box in the middle, and then another black box at the rightmost.

Here's my code so far. CSS:

```
* {
	padding: 0px;
	margin: 0px;
	}

a{
	color: #4D6DF3;
	font-family: Trebuchet Ms, Arial, sans-serif;
	font-size: 15px;
	}

body {
	background-color: #000000;
	}

hr {
	color: #000000;
	background-color: #000000;
	}

p, .pMirror {
	color: #FFFFFF;
	font-family: Trebuchet MS, Arial, sans-serif;
	font-size: 15px;
	padding: 8px;
	}

.main_matter {
	position: absolute;
	margin-top: 10px;
	}

.head {
	font-size: 34px;
	font-weight: bold;
	font-family: Arial, Helvetica, sans-serif;
	color: #FFFFFF;
	text-shadow: #000000 0px 0px 10px;
	}

.navigation{
	background-color: #787878;
	margin-left: 5px;
	padding: 8px;
	width: 190px;
	}

.body_text {
	margin-left: 230px;
	top: 40px;
	width: 40%;
	}

.main_section {
	background-color: #464646;
	margin-left: 20%;
	margin-right: 20%;
	padding: 10px;
	margin-bottom: 0px;
	height: 100%;
	}
```

My HTML file:

```
<html>
<head>
	<title>Sample Page</title>
	<link rel="stylesheet" type="text/css" href="kode.css" />
</head>
<body>
<div class="main_section">
	<span class="head">Banner</span>
	<hr noshade="noshade" />
	
	<div class="navigation pMirror main_matter">
	Navigation goes here
	<hr noshade="noshade" />
	Just some links.
	</div>
	
	<div class="body_text pMirror main_matter">
	<p>Just the standard Lorem Ipsum here (see images). Omitted for the sake of brevity.</p>
</div>
</body>
</html>
```

Any ideas? Thanks!

---

### Post by Reiger on 2010-10-30
This has to do with the box model.

Position absolute is rendered in its own box model (that is: the boxes generated absolute are not taken into account in the box calculations of the parent element if that element has a different [e.g. relative] model). Same for floated boxes.

As a result position absolute is simply not usable for large volumes of text which must scale or scroll as may be needed.

So you will need to rethink your use of the &#8220;main_matter&#8221; class.

---

### Post by r-senior on 2010-10-30
Without trying this I'm not sure if it would work, but have you experimented with "height: 100%"?

Alternatively, a 1px high background image set to repeat in the y direction could do the job?

---

### Post by skytreader on 2010-10-30
@r-senior
Yep. What's shown above is the effect of "height: 100%;". It shows the box with a height of 100% of what is *initially visible*. (Hence it breaks upon scrolling).

From Reiger's hint I removed main_matter all together and manually (through CSS), set the position of navigation and body_text. It did the trick.

Thanks.

---


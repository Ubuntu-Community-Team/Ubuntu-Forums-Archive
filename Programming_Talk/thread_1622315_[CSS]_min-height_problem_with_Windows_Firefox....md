---
title: "[CSS] min-height problem with Windows Firefox..."
date: 2010-11-15
forum: Programming Talk
---

### Post by skytreader on 2010-11-15
Hi all. I'm having problems with CSS min-height under Firefox. I'm seeing it in Windows and I haven't checked under Ubuntu (yet). Anyway, I'll be posting screen shots of what I see as well as my code.

So, in Chrome (which displays what I expect to see), I see this:
[IMG]http://www.skytreader.net/images/chrome.png[/IMG]

However, in Firefox 3.6, I see this:
[IMG]http://www.skytreader.net/images/firefox.png[/IMG]

My CSS code (I'm posting everything, just in case. However, to cut things short, I think what might come into play here are the rules .navigation, #pagetext, and .main_section, found below):

```
* {
	padding: 0px;
	margin: 0px;
	}

a{
	color: #4D6DF3;
	font-family: Arial, Helvetica, sans-serif;
	font-size: 15px;
	}

a.nav{
	color: #FFFFFF;
	font-family: Arial, Helvetica, sans-serif;
	font-size: 15px;
	cursor: pointer;
	text-decoration: underline;
	}

body {
	background-color: #000000;
	}

h2 {
	font-family: Arial, Helvetica, sans-serif;
	color: #FFFFFF;
	}

hr {
	color: #000000;
	background-color: #000000;
	}
	
img {
	border-width: 0px;
	}

p, .pMirror {
	color: #FFFFFF;
	font-family: Arial, Helvetica, sans-serif;
	font-size: 15px;
	padding: 8px;
	text-align: justify;
	}

.head {
	font-size: 34px;
	font-weight: bold;
	font-family: Arial, Helvetica, sans-serif;
	color: #FFFFFF;
	text-shadow: #000000 0px 0px 10px;
	text-decoration: none;
	margin-top: 0px;
	}

.navigation{
	background-color: #787878;
	margin-left: 1%;
	margin-top: 15px;
	padding: 8px;
	width: 25%;
	float: left;
	}

#pagetext {
	margin-left: 29%;
	padding: 10px;
	width: 70%;
	}

.main_section {
	background-color: #464646;
	margin-left: 20%;
	margin-right: 20%;
	bottom: 0px;
	padding: 10px;
	min-height: 100%;
	}
```

I've already tried adding height:100% in main_section . It isn't a very neat idea, however; it looks fine if the user doesn't vertical-scroll. Once he does, the box cuts-off, letting the text trail into the black background.

Any ideas?

---

### Post by worseisworser on 2010-11-15
Hi,
Do you have a link to the site? Just having it pop up instantly in Firefox+Firebug would be convenient for anyone trying to help.

---

### Post by skytreader on 2010-11-15
>.< My bad... I intended to put the HTML code of the page as well but I forgot. It's online now anyway at

[http://kode.skytreader.net/sample.html](http://kode.skytreader.net/sample.html)

And also, I have tested it with Google Chrome and Firefox Ubuntu now; the same results happen.

Thanks!

---

### Post by mcduck on 2010-11-15
Try adding "position: absolute;" to the .main_section. :)

edit: another option is to add "height: 100%;" to body.

Either way the problem is that the min_height is calculated from the height of the parent element (on your page "body"). But you haven't actually defined any height for body.

edit2:
[http://css-discuss.incutio.com/wiki/Hundred_Percent_Height]("http://css-discuss.incutio.com/wiki/Hundred_Percent_Height")

---

### Post by skytreader on 2010-11-15
Thanks mcduck. I used your position: absolute; suggestion. Works like a charm.

[EDIT] Just for anyone who might bump into the same problem later on and find this thread; I didn't put it in .main_section . Doing so caused some problems in pages wherein the user would have to scroll down. I put it in the body rule.

(Maybe, as I add more pages to the site and other bugs pop up, I'll be tinkering with the body rule)

> Either way the problem is that the min_height is calculated from the height of the parent element (on your page "body"). But you haven't actually defined any height for body.

---


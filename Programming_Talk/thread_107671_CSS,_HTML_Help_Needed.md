---
title: "CSS, HTML Help Needed"
date: 2005-12-23
forum: Programming Talk
---

### Post by audax321 on 2005-12-23
Hello,

I'm trying to make a website using CSS and I can not get anything to line up properly on both Firefox and Internet Explorer and it's driving me INSANE!!!!

Could someone please take a look at it? The files in the zip are as follows:

images (directory): contains images :)
index.html: this is the main page for the website
[INDENT]index.css: this is the CSS for index.html[/INDENT]
main.html: this page is supposed to open within index.html in an iframe
[INDENT]mainFrame.css: this is the CSS for all pages opening in the iframe[/INDENT]

Any help is appreciated. I plan to use the website to host some programs I've written for both Windows and Linux as well as some useful scripts so other people can use them as well!

Here is what I have so far: [http://www.dieburnbot.com/website_template.tar.gz]("http://www.dieburnbot.com/website_template.tar.gz")

---

### Post by majikstreet on 2005-12-23
o_O I suck with design but I wanted to say something:
the differences between browsers and oses are AMAZING. In firefox on linux a site looks great, but on firefox on windows it sucks.. I dunno why... and of course in IE it sucks..

-m

---

### Post by audax321 on 2005-12-23
I actually had it looking perfect in Firefox and Opera, but it was unusable in IE. So I rewrote it and now it looks equally messed up in both Firefox and IE. The header and footer look good, but the three center parts are completely unaligned and I'm not sure how I would add content to them.

---

### Post by DirtDawg on 2005-12-23
IE is the problem. Browse this interesting article:
[http://www.howtocreate.co.uk/wrongWithIE/](http://www.howtocreate.co.uk/wrongWithIE/)

---

### Post by audax321 on 2005-12-23
So are you saying there is no way to get this to work in IE? I know it has rendering issues, but at the point it is currently at, it has the same issues in Firefox and IE.  I uploaded it here if you want to take a look: [www.furrsoft.com/new_furrsoft/index.html](www.furrsoft.com/new_furrsoft/index.html)

---

### Post by sapo on 2005-12-23
[QUOTE=audax321]So are you saying there is no way to get this to work in IE? I know it has rendering issues, but at the point it is currently at, it has the same issues in Firefox and IE.  I uploaded it here if you want to take a look: [www.furrsoft.com/new_furrsoft/index.html](www.furrsoft.com/new_furrsoft/index.html)[/QUOTE]
There is, but maybe you will have to CHANGE your original layout/idea, to make it work with everything.

try the famous IE HACK:

if you put an underline before the css tag, just IE will read that tag, and the other browsers are gonna read the one without the underline, like this:

table {
_width: 750px;
width: 780px;
}

firefox, opera, etc will read the 780px, and IE will read 750px.

I sometimes have to do this UGLY workaround.. just try it out, it should work with almost all the css properties :P

---

### Post by DirtDawg on 2005-12-23
Well, it's a pain in the tookus, but here's a work-around I found that works. Maybe it will help you.

```

 Someone in September had asked a question about emulating frames with css fixed property and its compatibility with IE6. Here is how to do it

1. In your main style sheet, set margin and padding to zero (needed for the following internet explorer hack) and declare the desired positioning like this:

body
{
margin: 0;
padding: 0;
}
div.nav {
position: absolute;
top: x;
left: y;
}
body>div.nav {
position: fixed;
}
2. For internet explorer 6, make a second style sheet and remove the scroll mechanism from the root element and assign it to the document body; position:absolute will work like position:fixed now.

html
{
overflow: hidden;
}
body
{
height: 100%;
overflow: auto;
}
3. In the head element call the style sheet for internet explorer after the main style sheet using the 'conditional comment', like this:

<link ... >//themain stylesheet
<!--[if IE 6]>
<link ... >//IE hack stylesheet
<![endif]--> 

```

---

### Post by audax321 on 2005-12-23
Okay, now I'm really confused ;)  I'm not a web developer by any means, this is just a hobby. I thought the only problem I had was that in index.html, the following part was a bit out of order:

```

<div id="side_left">
	<div id="side_left_content">
		left: dhtml menu code here
		<div id="main">
			<div id="main_content">
				mid: iframe goes here
				<!-- <iframe src="main.html" name="mainFrame" width="566" height="364" align="middle" scrolling="auto" frameborder="0" style="z-index:3">Your web browser does not appear to support frames, please upgrade to a newer version.</iframe> -->
				<div id="side_right">
					<div id="side_right_content">right: java news applet</div>
				</div>
			</div>
		</div>
	</div>
</div>

```

Maybe I should just go back to what I know... ugly tables :(

I actually used [www.spreadubuntu.com](www.spreadubuntu.com) 's html code as a guide for this, but it only had one center section, mine has three positioned horizontally and this is where I am running into a problem. It looks like I might have to come out with a different way to lay this out after all.

---

### Post by DirtDawg on 2005-12-23
Hmmmmmm. I'm no wizard myself, but I'm having a little difficulty understanding what's happening. Is the blue center piece one graphic, or is it split in three parts? It looks like seperate parts. If that's the case, I would recommend creating one, large blue rectangle there, then creating an orange strip, or long rectangle to place on top of that (this can be done with a "z index", which allows layering. I believe the lower the value of z, the lower the layer it's placed on). This may help. 
Here's first thing I found on Google: [http://www.w3schools.com/css/pr_pos_z-index.asp](http://www.w3schools.com/css/pr_pos_z-index.asp)
There's plenty more.

On another note, I would recommend sticking with CSS as much as possible. I built [this website]("http://www.weeklyhilarity.com") using tables (I also had no idea what I was doing) and now wish I had used CSS as tables are unweildy and difficult to update. I ran into CSS problems with IE as well and I'm trying despretly to remember the fix. It may have been simply positioning things with "auto", but I really can't remember. I'll mill over it and if I remember you'll be the first to know.
Keep it up, I think the color scheme you chose is great.
Good Luck

---

### Post by audax321 on 2005-12-23
Yup, the center piece is three separate images. I'm going take a little break from this and try again later.  It would be funny to see all the developer's on the internet just get up and stop supporting IE, then everyone would use Firefox or Opera and the world would be a happier place... maybe... ;)

---

### Post by audax321 on 2005-12-23
I gave up on the other design and decided to make a new one. I think it turned out better than the other one and is working on both browsers!

[www.furrsoft.com/new_furrsoft/index.html](www.furrsoft.com/new_furrsoft/index.html)

Now, I just have to work on the content...

---


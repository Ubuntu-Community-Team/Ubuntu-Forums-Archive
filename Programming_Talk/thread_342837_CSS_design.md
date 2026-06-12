---
title: "CSS design"
date: 2007-01-20
forum: Programming Talk
---

### Post by WiseElben on 2007-01-20
Hi, I'm trying to solve a problem with a new CSS-based design I'm trying to make. I want a two column look, like the one in my current website [wiseelben.com]("http://wiseelben.com"). I've never figured out how to make both the body and the right column have the same height, regardless of amount of content. On this current design, I cheated by using a combination of tables and CSS, but I want to go for a pure CSS design. Here is my current body:

```

<body>
	<div id="structure">
		<div class="header">header</div>
		<div class="nav">nav</div>
		<div class="body">body</div>
		<div class="right">right</div>
		<div class="footer">footer</div>
	</div>
</body>

```

And the CSS sheet I've made:

```

body {
	background: #000000;
	color: #FFFFFF;
	font: Verdana, Arial, Helvetica, sans-serif;
	font-size: 11px;
}

#structure {
	width:780px;
	height: auto;
	margin-left: auto;
	margin-right: auto;
	text-align: left;
}

div.header {
	background: #006699;
	color:#000000;
	width: 780px;
	height: 100px;
	position: absolute;
	top: 0px;
}

div.body {
	background: #33FF33;
	width: 580px;
	position: absolute;
	top: 120px;
}

div.nav {
	background:#FFFF33;
	width: 780px;
	height: 20px;
	position: absolute;
	top: 100px;
}

div.right {
	background: #ff0000;
	width: 200px;
	position: absolute;
	top: 120px;
	margin-left: 580px;
}

div.footer {
	background: #FF99CC;
	width: 780px;
	height: 20px;
	margin-bottom: 20px;
}

```

Also, what is the best way to make the footer be in the correct position, where it would just dynamically stack below the body and right column?

---

### Post by Grey on 2007-01-20
min-height would be the correct way of doing that.  But you sacrifice IE compatibility by doing that, as IE6 does not support that.

I am a near guru level web programmer.  (I suck at design, but if you give me a photoshopped image of what it's supposed to look like, I can pull it off).  My personal website is entirely CSS based, and I believe it works in IE as well.  You can examine that for some ideas.

[http://grey.drunkencoders.com](http://grey.drunkencoders.com)

EDIT:  Ah yes, I remember now.  My solution to the IE problem was to hide the CSS from IE.  IE users should see plain text IIRC.

---

### Post by mssever on 2007-01-20
> **WiseElben said:**
> Also, what is the best way to make the footer be in the correct position, where it would just dynamically stack below the body and right column?
I'd do something like this:
```
<div style="clear:both; height:1px">&nbsp;</div>
<div id="footer">blah blah</div>
```Of course, in real life I'd pull the CSS out of the tag and use a class or ID.

---

### Post by lloyd mcclendon on 2007-01-20
> **Grey said:**
> I am a near guru level web programmer. 

LOL don't be so modest

your website is full of errors

XML Parsing Error: not well-formed
Location: [http://grey.drunkencoders.com/projects.php](http://grey.drunkencoders.com/projects.php)
Line Number 69, Column 32:
<label>Source:</label><span<a href="projects/clanocr.rar">0.1</a></span><br />
-------------------------------------^

---

### Post by Mirrorball on 2007-01-20
You can't do that (unless you ignore IE), you have to cheat. Search Google for "faux columns" and you will find loads of tutorials. And to keep the footer in its correct position, you can't absolutely position your columns. Float them instead (with the float property) and clear the footer (with the clear property). My advice would be for you to search Google, because although I know how to do this, I suck at explaining anything.

---

### Post by lloyd mcclendon on 2007-01-20
one of the guys at work needed to do this a few months ago, i think he settled on a javascript solution because he wasn't able to get anything going with pure css.  i'm sure it is possible though.

---

### Post by Mirrorball on 2007-01-20
It's possible with faux columns (a trick with backgrounds). Or ignore Internet Explorer and make your divs be displayed as table cells.

---

### Post by Grey on 2007-01-21
> **lloyd mcclendon said:**
> LOL don't be so modest

your website is full of errors

XML Parsing Error: not well-formed
Location: [http://grey.drunkencoders.com/projects.php](http://grey.drunkencoders.com/projects.php)
Line Number 69, Column 32:
<label>Source:</label><span<a href="projects/clanocr.rar">0.1</a></span><br />
-------------------------------------^

Oh bloody hell.  That'll teach me.  (There's no fancy form for updating the site.  I do it in a text editor, and typos do happen).

Nevertheless, there were two errors on the site.  One was the one you showed me, which was a missing right angle bracket, and the other was that I had embedded a pre inside of a p.  (I don't use pre a lot, and it was a careless mistake).  The CSS does not validate, but that's intentional.  The errors it complains about are because I am using vendor specific tags, and a couple of CSS3 tags.  The vendor specific tags that I use are done according to W3C specifications, so I don't consider them to be errors.  And honestly, CSS3 has been in drafting mode for far too long.  I am ready to use it damnit.

---

### Post by jblebrun on 2007-01-21
> **Grey said:**
> min-height would be the correct way of doing that.  But you sacrifice IE compatibility by doing that, as IE6 does not support that.

I am a near guru level web programmer.  (I suck at design, but if you give me a photoshopped image of what it's supposed to look like, I can pull it off).  My personal website is entirely CSS based, and I believe it works in IE as well.  You can examine that for some ideas.

[http://grey.drunkencoders.com](http://grey.drunkencoders.com)

EDIT:  Ah yes, I remember now.  My solution to the IE problem was to hide the CSS from IE.  IE users should see plain text IIRC.

Your website looks really cool for the split second before that eye-assaulting brick-like background loads! ;-)

---

### Post by jblebrun on 2007-01-21
> **Grey said:**
> 

[http://grey.drunkencoders.com](http://grey.drunkencoders.com)

EDIT:  Ah yes, I remember now.  My solution to the IE problem was to hide the CSS from IE.  IE users should see plain text IIRC.


Oh! Hey! You live in my city! Hi!

---

### Post by Grey on 2007-01-21
> **jblebrun said:**
> Your website looks really cool for the split second before that eye-assaulting brick-like background loads! ;-)

Hey, I told you that I suck at design.  =P  I just write the code.  I posted my site not so that you can admire the beauty of its appearance, but so you can view the source, and see that a purely CSS based design with semantic HTML can work.  (It's simple because I wrote the css in only a couple of hours.  But that's an advantage in this case, as the original poster would probably want to see a simple design, rather than a complex commercial design)

And hey, small world.  I'm actually Canadian though.  I just live here for the time being, and will likely be moving to LA at some point soon.

---

### Post by nagilum on 2007-01-21
Here's an in-depth tutorial on how to get a 3-column layout with equal-height columns:
[http://alistapart.com/articles/holygrail](http://alistapart.com/articles/holygrail)

---

### Post by Grey on 2007-01-21
That is incredibly clever.  That's all I have to say.  Never have I been so impressed since I first saw IE7 (the IE6 standards compatibility library, not the browser).

---

### Post by jblebrun on 2007-01-21
> **Grey said:**
> Hey, I told you that I suck at design.  =P  I just write the code.  I posted my site not so that you can admire the beauty of its appearance, but so you can view the source, and see that a purely CSS based design with semantic HTML can work.  (It's simple because I wrote the css in only a couple of hours.  But that's an advantage in this case, as the original poster would probably want to see a simple design, rather than a complex commercial design)

And hey, small world.  I'm actually Canadian though.  I just live here for the time being, and will likely be moving to LA at some point soon.


Well, my reaction wasn't necessarily to the design per se... I think the design is actually nice and clean. my design skills SUCK, so I always feel bad criticizing the design of others. 

But that background actually adds to the *difficulty* of reading the text on the page (For me, at least. Maybe I'm just a wus.)

---

### Post by kj1h234lkj1234 on 2007-01-22
> **jblebrun said:**
> Your website looks really cool for the split second before that eye-assaulting brick-like background loads! ;-)

I'm more worried about how badly that CSS causes Gecko to rape my CPU...

I gave up on web development because of Microsoft and the needless hoop-jumping required to make things work in their various products.

Good luck with CSS my friend! :D

---

### Post by Grey on 2007-01-22
> **kj1h234lkj1234 said:**
> I'm more worried about how badly that CSS causes Gecko to rape my CPU...

That's because of the opacity property.  (IIRC, it's been a while).  At any rate, it's significantly faster with modern gecko browsers.  (1.9 is smoking fast).  I was playing with a touch of CSS3 when I designed the graphics of the page.

---

### Post by WiseElben on 2007-01-22
Thanks for all the tips! I'll be researching and implanting this soon, hopefully.

Grey: I've seen your website somewhere... I think it was a link from the GameDev forums? =D

---

### Post by Dygear on 2007-01-24
Grey, I have a PSD layout for a site, if you think it's pretty good, you can use it.

I'm all for blue websites (look at [http://www.SimFIA.com/](http://www.SimFIA.com/)) but your's is much to blue and the brick layout makes it VERY hard to read. Here' take this color scyme, you'll like it...

```
body {
  background: #002040;
  color: #A0A0A0; /* Or #FFFFFF, if you want more readability */
}
h1, h2, h3, h4, h5, h6, .head, .header {
  color: orange;
}
a {
  color: orange;
}
a:hover {
  color: yellow;
}
a:active {
  color: white;
}
```

---

### Post by Grey on 2007-01-24
How about if I just increase the opacity on the text sections instead?  That would make the text sections a lot darker, and would make it easier to read.  I am not fond of the colour orange at all.  At any rate, I just increased the opacity on the text sections by 5% (bringing it to 95% opacity).  I think it should be a lot easier to read now.

But you know, that's the real beauty of CSS.  That basic layout, with the static header and the static right nav bar is REALLY easy to accomplish, and works in all browsers.  As a result, I've used it for other projects as well.  I think the one that I made that turned out the best was a pathetic library system mockup that I wrote for my software engineering class.  It had a brown colour scheme, and really turned out well.  If you remember the OLD Ubuntu themes, it was similar.  Not a hint of orange, and had a kind of an old parchment coloured background, and a darker chestnut colour for text areas(with white text of course).

**WiseElben**, I achieved my 15 minutes of internet fame a while back when I released the second version of Dissonance.  I've been forced to discontinue it since then because of an NDA.  But I gained a little bit of respect for a bit, so that's where you might have seen me.  :)

---


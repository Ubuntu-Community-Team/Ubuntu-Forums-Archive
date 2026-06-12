---
title: "Web game development with ubuntu"
date: 2010-09-29
forum: Programming Talk
---

### Post by Miles_Prower on 2010-09-29
I'm looking to sharpen my programming skills by throwing together a bunch of small web-based games (pong clone, tetris clone, etc etc).

Seems like flash would be a good way to get that done, but I don't think there are any linux-native development tools for flash.

html5 MAY work, and java also may work... is there an agreed upon standard, here?

---

### Post by myrtle1908 on 2010-09-29
> **Miles_Prower said:**
> html5 MAY work, and java also may work... is there an agreed upon standard, here?

Standard?  No.  You could look into Canvas or SVG.  Both are very capable for the graphics bit.  However, IE has no support for SVG and Canvas not supported in some browsers (can't remember which off the top of my head).

Personally I like SVG (or VML for IE).  Take a look at Raphael ... it's a nice JS vector drawing lib and pumps out SVG or VML depending on the browser.

[http://raphaeljs.com/](http://raphaeljs.com/)

---

### Post by lykeion on 2010-09-30
I think Flash sounds perfect for this (even though I'm a Java programmer myself). This might be a good read: _[Flash development in Ubuntu 10.04 with Eclipse and FDT]("http://www.brighthub.com/hubfolio/matthew-casperson/articles/73648.aspx")_

---

### Post by juancarlospaco on 2010-09-30
*nooooooooo flash nooooooooooooooo*  :)

---

### Post by dumbsnake on 2010-09-30
Hey,

If Steve Jobs hates it [Flash], it can't actually be that bad! Kidding aside, Flash is definitely the standard tool for this job. I work in game development and you'd be amazed how many games are written in Flash. However, you could write the types of games you mentioned using javascript as well. It would be a bit more work though. Goodluck!

---

### Post by simeon87 on 2010-09-30
Don't waste your time on Flash though, it's on the way out. Yes, I know it's the standard but if you're starting now, focus on the next generation of technologies. Make something with HTML 5 instead. It also saves you the hassle of developing Flash on Ubuntu...

---

### Post by worseisworser on 2010-09-30
I'd go for HTML5; i.e. canvas and JavaScript.

Neither Flash or Java "is" web ( [http://www.w3.org/](http://www.w3.org/) ) to begin with, and real web-stuff is starting to get interesting for games.

Install Chrome and try this:
  [http://mrdoob.com/projects/chromeexperiments/ball_pool/](http://mrdoob.com/projects/chromeexperiments/ball_pool/)


..things should be fast enough for a game now. :)

---

### Post by dv3500ea on 2010-09-30
You could use [OpenLaszlo]("http://www.openlaszlo.org/front_page"). It has an xml/javascript language and it compiles to both DHTML and SWF (Flash). It is available for Linux.

---

### Post by juancarlospaco on 2010-10-01
You can use Python  *(Django + S3 + EC2 + SimpleDB + ActionScript)*
i think.
:)

---

### Post by shadylookin on 2010-10-01
If you just want to do it as a hobby then do them in whatever you want(java applet/fx, flex, flash, html5/javascript). If you want to keep pace with actual web development then use html5/javascript which will probably replace flash for most things in the near future.

---

### Post by TinyXP on 2010-10-01
> **simeon87 said:**
> Don't waste your time on Flash though, it's on the way out. Yes, I know it's the standard but if you're starting now, focus on the next generation of technologies. Make something with HTML 5 instead. It also saves you the hassle of developing Flash on Ubuntu...

I agree.

You can make great apps with PHP, HTML5, JQuery and CSS3.

But if you wanna learn flash, you can install Macromedia flash 8 with wine and it works really well.

I can't wait for HTML5 because its such a smooth experience watching youtube videos on their HTML5 beta site.

---


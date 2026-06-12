---
title: "gambas2 connect to a website"
date: 2013-11-10
forum: Programming Talk
---

### Post by jamesfbays on 2013-11-10
I've installed gambas2 from the repositories. I've been playing with it for a couple of weeks, so I'm a gambas noob. My question is this: is there a command or an established function that I can use to connect to a website from within a gambas program. I would like to have a button or a link in my gambas2 program that will connect me to a chosen website. Thanks.

---

### Post by Tom_Carr on 2013-11-10
I was playing with gambas2, and someone suggested that I install gambas3.  I followed the instructions in this blog to do it.
[http://kalaharix.wordpress.com/](http://kalaharix.wordpress.com/)
According to this discussion, gambas2 is out of date.  

Things that did not work in gambas2 work fine in gambas3.  
I'm glad you are playing with gambas, because I am to, and I want someone to talk to.  I am starting a thread for general gambas questions so they will all be in one place and easier to find.

---

### Post by jamesfbays on 2013-11-10
For the moment I'll stick with gambas2. When I update to the next LTS, I'll probably move to gambas3. Anyway, I've already made my first gambas program (a rock, paper, scissor game) and it's pretty good. But what I really want to do is find a way to open a browser (the default browser) and open a web page. I'll keep looking, but if you come across something let me know. I'll try to keep in touch.

---

### Post by Tom_Carr on 2013-11-11
> [COLOR=#000000] I'll keep looking, but if you come across something let me know. [/COLOR]

Will do.  And if you find a forum of gambas users where I can ask a bunch of beginner questions, let me know.

---

### Post by kalaharix on 2013-11-11
I have not used Gambas2 in a long time but am sure there was a web-browser in the supplied examples. That should get you started.

It will probably load read-only. Just save as..  to another location so you can mess around with it.

---

### Post by kalaharix on 2013-11-12
It just struck me that you want to use a standard browser.

You can load a browser with a shell command for example:

Shell "chromium-browser http://www.bbc.co.uk"

This is in Lubuntu 13.10 gambas3 but I am sure it will work on Gambas2. At some stage the app name changed from google-chome to chromium-browser.

---

### Post by jamesfbays on 2013-11-17
Yes kalaharix, this is what I'm looking for. I've only tested this once, but it seems to work. I am going to find some documentation about the "Shell" command so I can understand it better. The question that I have for now is this: do I have to specify a browser, or is there a way to make this command find/access the default browser, whatever browser it might be (chromium, firefox, ice weasel, or whatever)? Thanks.

---


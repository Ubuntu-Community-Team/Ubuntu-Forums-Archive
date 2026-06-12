---
title: "clicking with javascript"
date: 2010-06-22
forum: Programming Talk
---

### Post by miak on 2010-06-22
Hi,

I was just trying to write a very simple code that will navigate to a certain page and click on certain location in the browser, preferably firefox.
After googling for some time I only found just chunks of code that were intended for somewhat experienced users. I'm completely new to javascript(or C#) or any language that will give possibility to do the task, but I know other not web-based programming languages, such as Java, C, python, so it shouldn't be hard to "explain" me what to do.

Thanks very much in advance,
miak

---

### Post by myrtle1908 on 2010-06-22
I'm not sure exactly what you are trying to do.  Do you simply want to automate Firefox?  Or crawl a page and simulate clicking a link?  If the latter, what do you intend to do with the content received by retrieving said link?

Greasemonky **may** help ... [http://en.wikipedia.org/wiki/Greasemonkey](http://en.wikipedia.org/wiki/Greasemonkey)

For HTTP comms and basic HTML parsing etc. there are many options eg. for Java you could go with Apache Commons HTTP Client [http://hc.apache.org/](http://hc.apache.org/) coupled with HTMLTidy [http://tidy.sourceforge.net/](http://tidy.sourceforge.net/) then throw in your own HTML/XML parser.

For Python there is the excellent Beautiful Soup. "Beautiful Soup is a Python HTML/XML parser designed for quick turnaround projects like screen-scraping"  ... [http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/)

---

### Post by miak on 2010-06-23
I'm basically trying to play an online game using a javascript, or whatever, you need to click at some locations on the screen, basically i want to do it as fast as possible ( by using a program to do it for me)

---

### Post by simeon87 on 2010-06-23
I'm guessing that such software already exists (the screen clickers).. not sure if they also include visiting a web page for you. I've never used any but perhaps you can find one for Ubuntu.

---

### Post by miak on 2010-06-23
I found "Kautoclick" that does autoclicking, but it can only click once in 200 milliseconds, is there anything faster?
Also I'd like to do the job with some programming to learn javascript.

---

### Post by BenAshton24 on 2010-06-23
This is actually really easy to do in python. This code should get you started. If you want to open Firefox first then use os.system or something.

```
#!/usr/bin/env python
import Xlib.display
import Xlib.X
import Xlib.ext.xtest
import time

display = Xlib.display.Display()
root = display.screen().root

def click(x, y):
	root.warp_pointer(x, y)
	Xlib.ext.xtest.fake_input(display,Xlib.X.ButtonPress, 1)
	display.sync()
	Xlib.ext.xtest.fake_input(display,Xlib.X.ButtonRelease, 1)
	display.sync()


# All of your different clicks can go here :)

click(20, 20)
time.sleep(2)
click(30, 20)

```

Hope this helps,
Ben.

---

### Post by miak on 2010-06-23
Thanks Ben,

That's exactly what I wanted.

---


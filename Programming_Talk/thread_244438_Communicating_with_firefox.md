---
title: "Communicating with firefox?"
date: 2006-08-26
forum: Programming Talk
---

### Post by Nytram on 2006-08-26
Hi,

I'd like to know is this is possible with Ubuntu - to use Python to read the current web page URL & title from Firefox?

(It doesn't have to be with Python, any language will do.)

Thanks,

Martyn

---

### Post by Pragmatist on 2006-08-26
> **Nytram said:**
> Hi,

I'd like to know is this is possible with Ubuntu - to use Python to read the current web page URL & title from Firefox?

(It doesn't have to be with Python, any language will do.)

Thanks,

Martyn

Does this help?
[http://www.python.org/doc/2.3.5/lib/module-urllib.html](http://www.python.org/doc/2.3.5/lib/module-urllib.html)

---

### Post by neilp85 on 2006-08-26
> **Pragmatist said:**
> Does this help?
[http://www.python.org/doc/2.3.5/lib/module-urllib.html](http://www.python.org/doc/2.3.5/lib/module-urllib.html)

It sounds like he wants to interface his Python code with Firefox, not just open an arbitrary url. That is a more difficult problem that I don't know how to solve.

---

### Post by dabear on 2006-08-26
I was unsuccessfull when I tried communicating with firefox through stdin..
I found the title in another way though:
xwininfo -all -root -children | grep firefox

---

### Post by nafai77 on 2006-08-26
The MozRepl plug-in will do exactly what you want to do.  Check out the homepage: [http://dev.hyperstruct.net/trac/mozlab/wiki/MozRepl]("http://dev.hyperstruct.net/trac/mozlab/wiki/MozRepl")

Feel free to ping me if you have specific questions.  I'm not the author of the extension, but I have some rough code that I have used to add a new bookmark to Firefox from the commandline.  I don't really have time to put it  up somewhere in a form that would be useable, but I might soon.

----

Travis
Read "musings in my software craftsmanship endeavors" [http://www.travishartwell.net/blog/]("http://www.travishartwell.net/blog/")

---

### Post by Nytram on 2006-08-28
I've had a quick look at the links and they look promising, i'll have a play around with them this w/e

Thanks guys,

---


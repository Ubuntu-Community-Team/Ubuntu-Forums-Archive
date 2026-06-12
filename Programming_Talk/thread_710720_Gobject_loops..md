---
title: "Gobject loops."
date: 2008-02-28
forum: Programming Talk
---

### Post by solarwind on 2008-02-28
Hey all,

I wrote a pyGTK program (written in Python) that uses gobject loops to execute a function every 60 seconds. However, there may be cases where the function gets stuck up somewhere and needs to be killed and restarted. What's the best way to keep a check on this? Would a watchdog type method work?

I was thinking along the lines of adding another gobject loop that runs a function every five minutes that removes the old gobject loop (the one that runs every 60 seconds) and adds it again. In that way, it's guaranteed to be restarted at least every five minutes. I know this is a very crude way but I can't think of any other method. I'm new to GTK and GOBJECT so any help would be much appreciated.

By the way, the program is a python mail checker that sits in the system tray. What happens is, sometimes (due to a bad internet connection), the connection times out or disconnects and reconnects. In this case, the mail checking function freezes up or crashes and the program just sits there doing nothing and I don't get notifications. However, restarting the program works but I don't want to have to keep an eye out for the program. It's supposed to be watching out for *me*!

I will gladly post the source code if anyone is willing to help me.

---

### Post by solarwind on 2008-02-28
Can someone please help?

---

### Post by nanotube on 2008-02-29
don't know much about gtk specifically myself, but...
why don't you run the actual internet-connecting-mail-checking steps in a separate thread, that then passes the info to your main thread (through a Queue, e.g.)? that way even if the net connection dies, your main gui thread doesn't get stuck.

---

### Post by solarwind on 2008-02-29
> **nanotube said:**
> don't know much about gtk specifically myself, but...
why don't you run the actual internet-connecting-mail-checking steps in a separate thread, that then passes the info to your main thread (through a Queue, e.g.)? that way even if the net connection dies, your main gui thread doesn't get stuck.

Good idea. Thanks!

---

### Post by solarwind on 2008-03-02
> **nanotube said:**
> don't know much about gtk specifically myself, but...
why don't you run the actual internet-connecting-mail-checking steps in a separate thread, that then passes the info to your main thread (through a Queue, e.g.)? that way even if the net connection dies, your main gui thread doesn't get stuck.

I tried the thread method but the thread stops when the app is running. It's weird, I don't know why.

---

### Post by imdano on 2008-03-02
Couldn't you just handle the exceptions (using try/except) that sometimes happen in your checking method, so that it always returns, even if it fails?

---

### Post by solarwind on 2008-03-02
> **imdano said:**
> Couldn't you just handle the exceptions (using try/except) that sometimes happen in your checking method, so that it always returns, even if it fails?

Tried that, it doesn't work the way I want it to... I still don't know why threading isn't working.

---

### Post by nanotube on 2008-03-02
> **solarwind said:**
> Tried that, it doesn't work the way I want it to... I still don't know why threading isn't working.

hm well post the source (or link to it) and maybe someone can take a look. :)

---

### Post by solarwind on 2008-03-02
> **nanotube said:**
> hm well post the source (or link to it) and maybe someone can take a look. :)

Well, this is for my gmail checker program. I don't need this anymore as I am using a different method now. Thanks for the help anyway guys!

If anyone's interested, my program is called ggmail [http://www.blog.solarwind.metafy.org/category/ggmail/](http://www.blog.solarwind.metafy.org/category/ggmail/)

---

### Post by nanotube on 2008-03-03
> **solarwind said:**
> Well, this is for my gmail checker program. I don't need this anymore as I am using a different method now. Thanks for the help anyway guys!

If anyone's interested, my program is called ggmail [http://www.blog.solarwind.metafy.org/category/ggmail/](http://www.blog.solarwind.metafy.org/category/ggmail/)

care to share this new method that worked for you?

(btw, your ggmail looks neat. :) )

---

### Post by solarwind on 2008-03-03
> **nanotube said:**
> care to share this new method that worked for you?

(btw, your ggmail looks neat. :) )

The new method is basically calling wget (instead of old urllib2 and sax method) with timeout options and checking for errors that way so the program doesn't get stuck up. If there is a network problem, wget will time out and return nothing in which case my program will detect that and try again later. Wget is so nice!

---


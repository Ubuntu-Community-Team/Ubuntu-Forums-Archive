---
title: "Building a panel / launcher."
date: 2008-04-07
forum: Programming Talk
---

### Post by BluntBox on 2008-04-07
Hey all. I'm just looking for some pointers / examples / suggestions to get me going in the right direction for a little project I have in mind.

As a learning experience in something other than CLI, I want to build a simple panel / application launcher. But I have absolutely no experience in drawing anything to the screen in Linux, or capturing mouse input for that matter.

Using C preferably, or Python (I don't know a lot of Python yet, but it seems easy enough to pick up so far). I've had a brief look at the pypanel source code, which makes use of both C and Python (any specific reason for this?). And from what I gather, uses Xlib and Imlib2 to display the panel and images. I did some googling on both those libraries, but a lot of results were very dated with obsolete methods etc. Are these the easiest libraries to use?

If anyone can to point me to some good reading material / examples on the matter I would be most grateful.

---

### Post by mike_g on 2008-04-07
Well from what I can tell so far most ubuntu linux programming seems to be done in C or Python. C is good for the intensive stuff, but Python allows for rapid development, probbly with less bugs in it too. So each are good for different tasks. 

I think you shoudl be able to make the panel launcher using Gtk+, or at least you can do all the other gui stuff with it. Its coded in C, so you wont need a wrapper for it. I started using it myself a couple of days ago and found it quite nice so far.

Edit: If you use Gtk the reference manual is handy:
[http://library.gnome.org/devel/gtk/unstable/](http://library.gnome.org/devel/gtk/unstable/)
I also found a nice book about Gtk/Gnome development here:
[http://freebooks.homelinux.org/](http://freebooks.homelinux.org/)

---

### Post by BluntBox on 2008-04-08
Continued to check out Xlib and Imlib2 after my first post. So far so good, I can make a window with no decorators etc and draw icons to it. First steps complete, now to get stuck in!

Thanks for the [http://freebooks.homelinux.org/](http://freebooks.homelinux.org/)  link, should be some interesting reading in that lot.

---


---
title: "Programming with x11"
date: 2005-09-07
forum: Programming Talk
---

### Post by rr00 on 2005-09-07
Hi, i am a newb to linux (ubuntu), so far its been easy to move win to ubuntu.I'm
a programmer and want to build apps that uses x11. Now, my box with ubuntu isnt
connected to net. So i cant get packages through synaptic. I downloaded lots of
stable lib x11 dev pakages from debian.org onto cd and tried to install then 'sudo dpkg -i ..'
some installed, but complain about verison 4.3 this, but the current is 6.8, and some is configured, or there is conflict....*sigh*. I knew dependencies will cause probs for me. So how should i proceed, to be able to use x11.

edt: im using freebasic compiler, and it needs x11 dev libs.

thanx.

---

### Post by toojays on 2005-09-08
Ubuntu's X server is quite different from Debian's so you need to get the one from archive.ubuntu.com, rather than debian.org. If you pick up the Ubuntu packages rather than the Debian ones, that will solve that problem.

As for programming for X11, it's almost always better to code for a GUI library rather than xlib. The only reason to use basic X11 is if you need to support some kind of lowest common denominator, or if you want to learn about X11. Otherwise, you are better off using wxWidgets, Qt or GTK.

---


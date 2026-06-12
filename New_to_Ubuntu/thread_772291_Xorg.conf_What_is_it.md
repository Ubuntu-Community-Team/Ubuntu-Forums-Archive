---
title: "Xorg.conf What is it?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by gentlemanmasher on 2008-04-28
I am not in coding and just was curious what this file is and what exactly am I doing when I sudo nano the xorg.conf file.

Again I'm not doing anything specific right now, but have for compiz-fusion in the past.  I guess I'm just curious as to what this file is and how what I'm doing is affecting the system.

Thanks

---

### Post by Tatty on 2008-04-28
X is the Windowing system (basically it sets the foundations for graphics on your system and allows for the creation of a nice GUI)

Xorg is i believe a free open source implementation of X

Xorg.conf is the primary user configuration file for xorg.

:)

---

### Post by Hospadar on 2008-04-28
This file sets up all the options for your video driver, and it also determines which video driver and extra video modules get loaded.  The file gets read every time you start an x server (but not once the server is already running)

An example of an xserver is your graphical desktop environment

---

### Post by Simpatico on 2008-04-28
When I modify xorg.conf, I usually need to change monitor refresh rates or the resolution.  Depending on the Linux flavor, sometimes that is possible only through xorg.conf.

---

### Post by martrn on 2008-04-28
Linux (which is a unix-like system) keeps its configration settings in its file systems, and thankfully doesn't use any redgistry hives or anything like that.

Your  Xorg.conf file is a configuration file for your X11 windowing system, that is the graphical user interface that drives the system you would call your Xwindows system.

It tell the X11 server, what mode to start you Xwindows session in, such as how big a screen you have you display resolution etc, etc....

---

### Post by Sef on 2008-04-28
> Xorg is i believe a free open source implementation of X

It is under the [X11 license]("http://en.wikipedia.org/wiki/X11_License").

---

### Post by gentlemanmasher on 2008-04-28
Excellent.  Thanks for the many great responses.

---

### Post by forrestcupp on 2008-04-28
It also has to do with input, i.e. your keyboard, mouse, etc.  We usually think of xorg.conf for video stuff, but X handles input, too.

---


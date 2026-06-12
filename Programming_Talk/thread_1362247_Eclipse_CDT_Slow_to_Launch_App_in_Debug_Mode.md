---
title: "Eclipse CDT Slow to Launch App in Debug Mode"
date: 2009-12-22
forum: Programming Talk
---

### Post by not_a_phd on 2009-12-22
I am using Eclipse Galileo CDT in Karmic. Generally like it with two quirky exceptions. 

1. When I debug an application (no matter how small), it takes an inordinate amount of time to launch. I push the debug button, and will generally see the Eclipse environment indicate that there is nothing to make (or incrementally compile a modified file). The environment then stalls at 57% progress for on the order of 30-60seconds. 

It is clear that Eclipse is *not* rebuilding my app. Even if it was, it would not take that long to recompile and link a 5-line hello-world. What is it doing? Is it trying to find a resource? Is there a fix that anyone knows of?

2. Eclipse will (sometimes) stop responding to my keyboard when I am away from the workstation long enough for it to go into screensaver mode. I have heard of (and experienced) the button bug, where Eclipse doesn't respond to mouse clicks. This is different. Has anyone else experienced this. I often have to bring Eclipse down and restart it to get it to respond to the keyboard again.

Thanks in advance.

---

### Post by not_a_phd on 2009-12-23
On the second quirk. Sometimes I will regain keyboard response by saving all and rebuilding. Not sure what that is all about, but my biggest issue is launch time during debug.

---

### Post by billiumb on 2009-12-27
Point 1 happens to me on Gentoo -- exactly the same 57%.

It is annoying. :)

Billy

---

### Post by not_a_phd on 2009-12-28
Happens  to a colleague of mine using CentOS. Anyone out there actually know what is sticking Eclipse at 57% during a debug launch??

---

### Post by Martin__ on 2009-12-30
I have the same problem on Karmic as well .

Some extra details: 
-Sun Java(TM) SE Runtime Environment (build 1.6.0_17-b04) 64 bits.
-In both KDE and Gnome.
-With and without compositing.
-Just a "Hello World" program.
-No suspicious CPU nor HDD activity.
-2.6.31-17-generic kernel.

---

### Post by eewoz on 2009-12-30
This problem gets discussed at [http://www.eclipse.org/forums/index.php?t=msg&th=156536&start=0&](http://www.eclipse.org/forums/index.php?t=msg&th=156536&start=0&).

---

### Post by not_a_phd on 2010-01-02
Thanks eewoz. Looks like the solution options are either to change the debug launcher from standard (giving up functionality), or to download the latest nightly build and installing the fixed debug tools from that.

---

### Post by Martin__ on 2010-01-03
Thanks!

---


---
title: "Creating a GUI program without a framwork"
date: 2010-04-19
forum: Programming Talk
---

### Post by vis.15 on 2010-04-19
I have been searching for articles/tutorials/anything on how to create a GUI program without using a framework. For example, I do Not want to use wxWidgits, or QT or anything like that. I have used all kind of frameworks like that before, mostly wxWidgits. Now, I would like to really program. Like talk to the kernel and send messages and events. Any help would be greatly appreciated.   


Note: I've been programming in C/C++ for a few years now.

---

### Post by phrostbyte on 2010-04-19
If you want to code directly to X.org, check out Xlib.

[http://tronche.com/gui/x/xlib/](http://tronche.com/gui/x/xlib/)

Xlib is basically as low as you can go with X.org. Yes you will be directly drawing lines and shapes and even getting and setting individual pixels. There is no widgets to be found!

You want to speak directly with the Linux kernel? Then you should bypass X.org entirely. There is no windowing system if you go this route.

You should then access the Linux Framebuffer Device. I don't know of the direct API for this, but I know this very thin library accesses it: [http://www.directfb.org/](http://www.directfb.org/)

And hey, it's FOSS, so you can see how it does what it does. :lolflag:

Good luck.

---

### Post by nvteighen on 2010-04-20
Any reason for doing this? I mean, like phrostbyte said, unless you want to write an alternative to X (using the framebuffer or not), you'll always be writing something within a framework...

IMO, trying to bypass the existing GUI toolkits is pretty unpractical unless you've found an important feature lacking in them or you just want to learn X's API for fun and knowledge. If the latter, well, go ahead, but forget about all the nice widgets, containers and etc. and start thinking on pixel-based GUI programming without any event system at all.

Trying to bypass X and to interface a GUI durectly with the Linux kernel sounds like something insane to me...

---

### Post by cdekter on 2010-04-20
I can't imagine why you'd want to do it... sounds like a world of pain. X programming is not easy to pick up and full of little quirks and idiosyncrasies.

---

### Post by Tony Flury on 2010-04-20
Building a GUI based appplication without using a framework would be trying to build a bicycle using a lump of iron ore and some rubber tree sap - no prebuilt wheels or gears or tubing, tyres etc, and no screws, bolts, nuts etc - and no jigs to make any of them - Everything including your tools have to made from scratch.

Good luck with re-inventing the wheel, tubing etc and the spanners, screwdrivers, wrenches, tyres, brakes, cables.

---

### Post by vis.15 on 2010-04-20
The main reason why I want to do this is so I can "look inside the wheel." I'm not really going to build a whole application. I just want to view and understand what's going on behind the seen. 

So far phrostbyte you have been a great help with the X.org programming. 

nvteighen, the reason is to learn.

So far I have build, one application using X.org's API and it is not that hard. (Technically I edited someone else's program.) I kind of like it; there is so much control.

---

### Post by nvteighen on 2010-04-21
> **vis.15 said:**
> 
So far I have build, one application using X.org's API and it is not that hard. (Technically I edited someone else's program.) I kind of like it; there is so much control.

Hm., maybe that's the best way to go: editing others' code. The thing is yes, you get a lot (almost all) of control, but at the cost of having to exercise that control in order to have even the most basic things working.

As far as I can tell, X.org programming nowadays is almost restricted to the creation of higher level GUI libraries. But, well, you've been warned :p 

Seriously now, good luck. If it's for learning, I can see the point of this; it will be a pain, but you may learn stuff that interests you (although I can't see anything of interest for me in there!).

---


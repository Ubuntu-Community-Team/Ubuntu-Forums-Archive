---
title: "X11 programming / driver model / even model"
date: 2010-04-18
forum: Programming Talk
---

### Post by vek on 2010-04-18
Greetings.  I'm working on an app which traps the mouse cursor in the visible screen(s) for those with multimonitors, to avoid the 'dead zone' problem.  I can't seem to find anything that already does that (And searching for 'trap mouse' or 'constrain mouse' comes up with too many unrelated queries.

I've already got a working app that does it at the high level, via mouse polling, XWarpPointer, XQueryPointer, but its just not the right approach to the problem.  Relying on polling 'works' but it eats up CPU (sometimes reaching 1 percent!) needlessly and still has flicker.  

What I'd like to do is get somewhere in-between the mouse driver and Xorg itself, altering the data before X gets it or at least as part of the event loop so that the mouse data is altered BEFORE it gets sent to the various windows / updates the hardware cursor.

However, my problem with this all is I can't seem to find a good place to start... XLIB seems still too high a level, and expertise on low level X11 / drivery stuff seems to be super rare.  I'm finding it difficult to get documentation, and even harder to get the big picture of how the whole data flow between Mouse -> Mouse Driver -> XORG -> WM works.

Is there a good site for finding X11 specific architecture stuff, or documentation of data flows, etc?  What source packages should I start looking in?  Even just a block diagram of who feeds events to whom would help.   Or perhaps a project has already been begun to address this issue and I can join it?  Any info would help, I just need some ends to pull at to get this ball unravelled.

---

### Post by xoros on 2010-07-02
I know it's not specifically X11 but did you check the source code for Mousetweaks?

It features... 
* pointer-capture applet: provides an area on the panel which temporarily locks the pointer

[https://launchpad.net/mousetweaks/](https://launchpad.net/mousetweaks/)

---

### Post by vek on 2010-07-02
Thanks for pointing out mouse-tweaks to me.  It appears to use polling and warping to move the cursor (which it hides) back to the middle of the widget, whenever it leaves the widget.  

I have already made a prototype Qt app which keeps the mouse cursor within the viewable area by a similar method of polling and warping, but unfortunately, you see it jitter around and warp and so on, so polling it is not an ideal solution.   I'd prefer to get in at a lower level and alter the input events so that the mouse is never allowed to escape the screen in the first place.

I'll keep looking, but thank you for the heads up.

---

### Post by xoros on 2010-07-03
You are welcome, I would be interested to find out how you ended up implementing what you are seeking with the mouse... if you would be so kind to share. 

I'm looking to try to do a similar thing on a more global level.

---

### Post by soltanis on 2010-07-03
I saw your post a while back, and lacking any experience in X I didn't say anything, but just my 2 cents, it sounds like what you're doing is best implemented as a patch of some kind against the X server itself, rather than at a lower level (driver) or higher level (app). This just seems to be the kind of thing that X should understand how to do -- don't put the cursor in locations where it just shouldn't be able to go, and I'm sure many people will appreciate something to that effect.

Of course X is a huge complicated mass of code, and I wouldn't know where to start.

---

### Post by vek on 2010-07-03
All I've found so far is that there are constraining functions in the X11 server layer, but the problem is that at that level, X11 doesn't "understand" the real layout, it still only sees the one large screen upon which the smaller virtual screen(s) are arranged.  That virtual screen stuff seems to occur at a higher level, which is probably why this is a problem.

in XOrg, the following are of interest in mipointer.c
miPointerCursorLimits
miPointerConstrainCursor

More info
[http://xwindow.angelfire.com/page9_4.html](http://xwindow.angelfire.com/page9_4.html)

When I get some time, I'll investigate some more.

---


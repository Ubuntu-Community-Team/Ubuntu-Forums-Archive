---
title: "driver to XORG input model - direction needed"
date: 2010-04-24
forum: Programming Talk
---

### Post by vek on 2010-04-24
Greetings.  I'm trying to find the part(s) of the system that connects the raw mouse input to the cursor on the screen.

For example, moving the mouse generates events (in /dev/input/mice and in other places).  Something is listening to those events, and through a series of processes, they end up with the final result of moving the X.ORG cursor around the screen.  I want to know what processes and modules are sitting in that unknown gap between the mouse driver and the cursor moving around on the screen.  What is the data flow?  What is it thats listening, and how does it work?

I've searched in vain for some sort of documentation on what module(s) lie between those two points, but it turns out that documentation is extremely sparse.  :(

My end goal is to modify cursor movement events before XORG applies them to the visible on-screen cursor - to provide a tighter control on mouse and touchpad movements.... which means I cannot rely on XORG apis, I have to work below that.  By the time XORG gets the event, it is already too late (unless some part of it gets to look at / modify the motion event before it actually moves the cursor?).

I just need a couple places to start looking, so far trawling through X11 docs is coming up empty as the vast majority of them deal with how a user making an application might make use of the event system, not how someone more interested in low level stuff might hook into and alter them BEFORE X uses them.  X documentation is sparse enough to begin with.  Maybe what I'm looking for is in the head of just one or two people out there...

To clarify:  XWarpCursor / XQueryCursor - its already too late by the time we're at the level of these APIs.  I might need to write a custom mouse driver or something (not afraid to do that) but at the moment I have no direction in which to start searching...

---


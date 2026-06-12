---
title: "best way to stack graphics in gnome panel applet?"
date: 2010-11-19
forum: Programming Talk
---

### Post by AKADAP on 2010-11-19
Background: I am attempting to write a gnome panel applet to show the status of the MythTV back end. I would like to overlay a red circle on top of another image when the back end is recording. I would like to overlay a number on top of the red circle when the back end is recording more than one program.

So far, I'm showing the icon for the panel applet beside the number of recordings using the hbox in a Python panel applet.

It looks like I could stack images & labels on top of each other with a "fixed" container, but that would mean that I would have to do all of the sizing and placement by hand.

Is the "fixed" container the right way to go? Or is there a better choice?

---


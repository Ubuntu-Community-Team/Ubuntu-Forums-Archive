---
title: "Trying out gnome-applets after compilation"
date: 2011-01-10
forum: Packaging and Compiling Programs
---

### Post by wakabakalaka on 2011-01-10
Hi,
 
 I'm trying to compile the gnome-applets package (specifically stickynotes applet) and modify a few things.

 The compilation appears to go fine, what are the next steps for trying out the applets?
 
Just for the hell of it I took the stickynotes_applet executable file and put it in my /usr/lib/gnome-applets/ folder (replacing the existing one - backed it up). However when starting the applet (by adding the icon to panel) it crashes straight away and asks me if I want to reload the applet. :confused:

One thing I've noticed is that my currently installed sticknotes_applet is around 51kb, whereas my compiled one is around 196kb... what would cause this? (libraries attached to the executable?)

Is there a special procedure for debugging applets like this? Thanks!

---


---
title: "Top panel (menu bar) moved to side of screen - how to move back?"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by neksys on 2008-09-08
Hi there,

My top menu bar (the one with Applications/Places/System) has somehow moved from the top of the desktop to the left side. I can't for the life of me get it to move back. I've searched the forums, and of the solutions provided, click and drag does not work , and going through and unchecking "Lock to Panel" on each element has not helped.  Any ideas?

---

### Post by rossjman1 on 2008-09-09
You should be able to drag the panel to the top. You can always add a new panel and drag and drop all the items from the old panel to the new one (after unlocking them of course).

---

### Post by Oldsoldier2003 on 2008-09-09
> **neksys said:**
> Hi there,

My top menu bar (the one with Applications/Places/System) has somehow moved from the top of the desktop to the left side. I can't for the life of me get it to move back. I've searched the forums, and of the solutions provided, click and drag does not work , and going through and unchecking "Lock to Panel" on each element has not helped.  Any ideas?

right click an empty spot on the panel, select properties. set the orientation dropdown to top.

---

### Post by rossjman1 on 2008-09-09
> **Oldsoldier2003 said:**
> right click an empty spot on the panel, select properties. set the orientation dropdown to top.
lol cant believe i forgot about that

---

### Post by anewguy on 2008-09-09
Or of course just hold the left button down while the mouse is over a blank space on the bar and just drag your mouse to where you want it.  When you let go of the mouse button the bar will go there........


Dave :)

---

### Post by John The Bad on 2008-10-01
Hi, the same thing happened to me -- I was messing around with the top panel and I dragged it to the right side.  Now I can't get it back.  There are no blank spaces for me to right click or to use for a drag.  Is there a properties file for the panel that I can edit and replace "right" with "top"?

---

### Post by terry_gardener on 2008-10-01
john the bad 

to change it from right to top. 

press alt+f2 
type "gconf-editor" press enter 
under app then panel, then toplevels, then click top_panel_screen0
find orientation and change it from right to top. 
then just close gconf-editor

---

### Post by blisterpeanuts on 2008-11-28
> **terry_gardener said:**
> john the bad 

to change it from right to top. 

press alt+f2 
type "gconf-editor" press enter 
under app then panel, then toplevels, then click top_panel_screen0
find orientation and change it from right to top. 
then just close gconf-editor

This is the best advice yet.  It's easy to screw up that d*mn menu and overly difficult to put it back.

---

### Post by haddog on 2011-02-21
> **terry_gardener said:**
> john the bad 

to change it from right to top. 

press alt+f2 
type "gconf-editor" press enter 
under app then panel, then toplevels, then click top_panel_screen0
find orientation and change it from right to top. 
then just close gconf-editor

This definitely is the best solution! TY terry_gardener!

---


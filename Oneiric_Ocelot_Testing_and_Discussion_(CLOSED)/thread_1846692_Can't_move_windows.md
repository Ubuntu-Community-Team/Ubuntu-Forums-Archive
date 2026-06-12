---
title: "Can't move windows"
date: 2011-09-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by NCLI on 2011-09-19
Anyone else? And yes, the "move windows" plugin is enabled in Compiz, and everything works fine with metacity.

---

### Post by fjgaude on 2011-09-19
What do you mean? Can't move an app window from one desktop to another or within the same desktop?

---

### Post by JKoder on 2011-09-19
> **NCLI said:**
> Anyone else? And yes, the "move windows" plugin is enabled in Compiz, and everything works fine with metacity.

I encounter the same. 
For example , open gnome-terminal, and other window ( nautilus )
Now, open and close Dash. After this you wont be able to move the top most window ... after ALT+TAB everything is working again.

 A bit annoying

---

### Post by TheNessus on 2011-09-19
do you use Chrome or Chromium?

I have found a strange bug, that when chrome\ium does not use system title bar, then Unity acts strange if you minimize it. The bug specifically is as if there is a ghost window on top of everything, and you can only pick windows through unity dock or alt-tab, but you can't choose a window from the screen itself because of the ghost window on top of everything. The bug does not happen if Chrom/ium does use system title bar. choosing a window from unity dock or alt-tab fixes it.

I tihnk this is related to the issue of maximizing chrome\ium: unity needs to remove the title bar of maximized windows, but if chrome\ium does not use system title bar, it conflicts with something.

---

### Post by NCLI on 2011-09-20
The only way I can get it to work is by using Unity 2D... Guess it's bug filing time.

---

### Post by mc4man on 2011-09-20
If you minimize any window in unity all sorts of bad behavior can happen
This will be fixed in the next compiz upgrade

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/847967](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/847967)

---


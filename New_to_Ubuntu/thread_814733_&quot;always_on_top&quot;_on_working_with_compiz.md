---
title: "&quot;always on top&quot; on working with compiz"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by noorez on 2008-06-01
Hi, I'm trying to set some of my windows with "always on top" but it does not work. Other windows will still cover the window that i set to "always on top". Is there a setting that have to put on compiz in order for this to work?

---

### Post by NikoC on 2008-06-01
System > Preferences > Advanced Desktop Effects Settings > Window Rules

Make sure that you activate this plugin and then in 'Window Rules' copy/paste the name of the app you want on top in the box following 'Above'.

e.g. for gnome-terminal to always be on top copy/paste the following line in the Above box:
name=gnome-terminal

Cheers

---


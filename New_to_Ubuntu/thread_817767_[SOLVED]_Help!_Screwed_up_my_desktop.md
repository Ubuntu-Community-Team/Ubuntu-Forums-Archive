---
title: "[SOLVED] Help! Screwed up my desktop"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Confazed on 2008-06-03
I recently installed openbox and was playing around with it, then I installed the most recent "important updates".  I switched back to metacity and then did the required restart and all of the sudden my desktop looks like the attached picture.  I can't right click on the break seen in the picture or move icons onto it.  I do startup with conky and the horizontal offset is exactly the size of my conky window (conky starts up in the outer box). 

What did I do and how can I fix it?  

I use dual screens and use the command xrand to get them to display with a large virtual screen.

I tried uninstalling conky, but it still starts up with the same break.

---

### Post by Confazed on 2008-06-04
I tried the following:

sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session

sudo aptitude reinstall ubuntu-desktop

but still no luck.

Watching the restart it appears that it's part of the start up (the regular screen shows up initially, and then the weird second box comes later.  Even after the command to set up the second screen.

---

### Post by Confazed on 2008-06-04
Solved by deleting all of my config files for gnome and metacity

---


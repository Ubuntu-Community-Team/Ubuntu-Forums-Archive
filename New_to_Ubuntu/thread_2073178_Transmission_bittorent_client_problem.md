---
title: "Transmission bittorent client problem"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by GutsyRabbit on 2012-10-19
After installling Ubuntu Studio, i installed KDE.. since i like it more than the Gnome shell.
when i used Transmission bittorrent client, the KDE's window manager got replaced with the Gnome's WM.
I noticed this when my desktop changed to gnome style - no icons, no wallpaper, and when i right click, it shows me the gnome menu, also the icon for managing kde widgets from the right upper corner is gone to.. only the KDE taskbar remains untouched.
Is there any way to avoid this, or should i use another bittorrent client?

---

### Post by AlexDudko on 2012-10-19
Try to delete .gconf and .kde folders in your home directory (these folders are hidden) and restart the  system.

---

### Post by GutsyRabbit on 2012-10-19
i restarted the computer without deleting those 2 folders, to see if they are to blame.
KDE works normal now , and transmission didnt crash the WM this time, i actually tried to open a folder from a torrent within transmission, it opened nautilus, after i closed nautilus, that's when i saw the WM changed.. maybe nautilus was too blame..
anyway *hugs* thanks for the reply. ^^

---


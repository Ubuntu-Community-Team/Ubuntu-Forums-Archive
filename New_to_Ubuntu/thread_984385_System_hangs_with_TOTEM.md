---
title: "System hangs with TOTEM"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by gurpal123 on 2008-11-16
My system hangs frequently with Totem media player running, especially when I am connected to net. Many of times I had to **switch off** the system. I stopped using Totem as for now, what I would like to know, is there any tool like task manager in windows, to end the non-responding programs, I am aware of **System Monitor** and **Force Quit** features, but nothing seems to work when the system hangs completely, moreover there are no keyboard shortcuts for either of these....:(

---

### Post by MasterSander on 2008-11-16
Try ctrl+alt+f1, this should bring up a terminal unless your system is totally hung. You can then enter top to view processes and use killall to kill a certain process or kill and then the proces ID.

The reason why totem hangs is possibly because of the video output, try to see if you change it, I know you can in VLC, my system used to hang also because of VLC and I changed video output to openGL

---

### Post by markharding557 on 2008-11-16
Click on the add to panel in taskbar and add force quit.
check if totem freezes on video and then test it on audio only to see if it does the same this will start you in the direction of trouble shooting the problem

---

### Post by gurpal123 on 2008-11-23
Hey thanks Sander, your ctrl+alt+f1 technique did help, but then how do u return to desktop, in GUI mode... I had to restart the system.

---

### Post by Malta paul on 2008-11-23
ctrl+alt+F7 should work

---


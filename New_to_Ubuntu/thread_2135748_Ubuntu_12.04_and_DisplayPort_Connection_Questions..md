---
title: "Ubuntu 12.04 and DisplayPort Connection Questions."
date: 2013-04-15
forum: New to Ubuntu
---

### Post by zemega on 2013-04-15
Hi. I would like to enquire whether Ubuntu 12.04 supports DisplayPort Connection well or not. The point in using DisplayPort, is that you only going to need one connection port in the CPU, using a special adapter specifically for DisplayPort, and you can connect several monitors (using DisplayPort connection) to that adapter, and just one connection to the CPU. I'm enquiring about this, because my supervisor wanted a new CPU with multiple monitor connected to the computer. I know that you can just put in several video cards inside the computer, but that would just ignore the benefit and technology of DisplayPort. And since the liscense of DisplayPort is free, Ubuntu or Linux must have work on DisplayPort. I have no brand of monitor, CPU, or the adapter yet, as I would like to know whether the basic support for DisplayPort is working or not, including the multiple connection using adapter. I know HDMI works, but HDMI doesn't have that multiple function as far as I know.

---

### Post by 3rdalbum on 2013-04-15
Yes, Displayport is supported, but if you use an ATI or Nvidia graphics card you'll probably need their respective proprietary drivers. The open-source ATI and Nvidia drivers do support Displayport, but it might still be a little experimental.

The proprietary drivers should be fine though.

No idea about the multiple connection thing; it should probably work, but I don't think you'll be able to hotplug.

---

### Post by zemega on 2013-04-15
What do you mean by hotplug? So its best to recommend Intel graphic cards? Just to be clear, we won't really need state of the ark graphic card. Neither are we doing anything graphic heavy. We're focused on data analysis, graphical data to be precise, with lots of plots making. So the extended display is for comparing the plots mainly. The PC, or rather HPC actually, probably multiple cores, and maybe 16GB RAM. I think my supervisor prefers Dell, for the enterprise technical support and simplicity.

---

### Post by zemega on 2013-04-15
Bump?

---

### Post by 3rdalbum on 2013-04-16
Hotplugging is to plug in a monitor while the computer is on. You can't really do that on Linux.

ATI, Nvidia or Intel will be fine. Nvidia and Intel are preferred in general.

---

### Post by zemega on 2013-04-16
So, you can't do that in Linux, now I know. Does that mean plugging in a different monitor? Because I frequently disconnect a monitor from a running Suse 11 and use it with my laptop, then plug it back to the original computer. There was no problem.

---


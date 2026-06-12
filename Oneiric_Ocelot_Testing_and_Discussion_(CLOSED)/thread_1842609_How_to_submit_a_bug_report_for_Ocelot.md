---
title: "How to submit a bug report for Ocelot"
date: 2011-09-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by makitso on 2011-09-11
I have never been good at submitting ubuntu bug reports.  However, the beta release is failing to detect the video card for my thinkpad t60 -- which is an intel 945GM.  What package would one file the bug on?  For what its worth, a lspci does show the device.  It's an issue because I get into fall back mode on the gnome 3 shell.

---

### Post by linuxman94 on 2011-09-11
From my research, that card is too old for gnome3 and it will automatically go into fallback mode.

---

### Post by makitso on 2011-09-11
Not true.  I can boot up  the latest Fedora with the gnome 3 shell and it works fine and its noted in the system information display.   In the System Info, under the Graphics tab, it lists Driver Unknown.  On Fedora it list Intel 945.  When I log into Unity, its not in fall back mode, I have full 3D graphics support.  Something is hosed.

---

### Post by jbicha on 2011-09-11
Run ubuntu-bug and choose display problem. That should automatically open a form for you to submit the bug in the right place and attach a bunch of log files and other info about your system to help the bug triagers and developers.

---

### Post by cariboo on 2011-09-11
> **linuxman94 said:**
> From my research, that card is too old for gnome3 and it will automatically go into fallback mode.

 You better not tell my netbook that it won't work, with the Intel 945 chipset, it runs Unity and Gnome-shell without any problems.

---

### Post by makitso on 2011-09-12
I filed the bug.  Cariboo, that is good news.  If you look in the System Info / Graphics tab does it show the 945 or driver unknown?  This may be something unique to the thinkpad t60.

---

### Post by cariboo on 2011-09-12
> **makitso said:**
> I filed the bug.  Cariboo, that is good news.  If you look in the System Info / Graphics tab does it show the 945 or driver unknown?  This may be something unique to the thinkpad t60.

I'll have to check tomorrow, as the netbook battery died, and I left the charger in the shop. Check to see if the i915 driver is loaded:

```
lsmod | grep i915
```

---

### Post by makitso on 2011-09-13
Bug fixed with kernel update 3.0.0.11

---


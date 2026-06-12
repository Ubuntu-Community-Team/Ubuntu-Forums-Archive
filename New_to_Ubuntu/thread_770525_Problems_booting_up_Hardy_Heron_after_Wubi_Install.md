---
title: "Problems booting up Hardy Heron after Wubi Install"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by kraftwerk-it on 2008-04-27
I’ve downloaded the Hardy Heron .iso from Canonical and burned it onto CD (and the .iso size and CD size would appear to be OK). When I pop the CD in my drive, the Ubuntu CD Menu pops up. I have chosen to go down the Wubi route, and everything goes fine, until I reboot and try to start Ubuntu.  The progress bar goes about 15% along the bar and stops. After several minutes I tried Ctrl-Alt-Del, and then the progress bar jumps to roughly 85%. After several minutes of waiting, I do another Ctrl-Alt-Del, which then reboots my PC. The same thing happens if I mount the .iso and run Wubi from that. 

In verbose boot, the hang points are 54.64756 and 118.68874.

Here’s my system configuration:
Processor: 
Intel(R) Core(TM)2 CPU 6420  @ 2.13GHz
System BIOS : 
American Megatrends Inc. P1.60
Mainboard: 
AsRock ConRoe945G-DVI
Physical Storage Devices: 
HDT722525DLA380 250GB (SATA150, 2.5", 7200rpm, NCQ, 7MB Cache) : 233GB (C:)
SAMSUNG HD501LJ 500GB (SATA300, NCQ, 16MB Cache) : 466GB (D:)
ATAPI DVD A  DH20A1S (SATA150, DVD+-RW, CD-RW, 2MB Cache) : N/A (Y:)
Memory Module 1 & 2: 
Team-Value-667 1GB PC2-5300U DDR2-333
OS:
Vista Home Premium SP1

Could the headache be caused by the fact that all my drives are SATA? Or is it just a question of a bad d/load?

---

### Post by GepettoBR on 2008-04-27
The fact that your drives are SATA shouldn't matter. I've installed Ubuntu in SATA and IDE drives with no problem (granted, I've never used Wubi). Have you tried waiting it out? The first boot can be very slow sometimes (I have no idea why, but it happens).

---

### Post by hackle577 on 2008-04-27
You might try just booting to the Ubuntu CD and reinstalling from there. Wubi seems to be giving a lot of people problems.

---

### Post by Solrac924 on 2008-04-27
try burning it again at a slower rate. that's what happened to me the 1st time.

---

### Post by kraftwerk-it on 2008-04-27
Thanks for the suggestions.

GepettoBR: I haven't tried waiting it out, since I thought slow bootups are confined to Windows :-) and I thought that with my h/w, 5 minutes should be enough, but will try it later today.

Hackle577: I would prefer to install Ubuntu into a dedicated partition, but with the amount of data I would need to back up (and the time involved) before repartitioning I thought I'd give Wubi a try. Seems that I've now spent more time battling Wubi than it would have taken me to back up and repartition!

---

### Post by kraftwerk-it on 2008-04-27
Solrac: I'll try that as well. Thanks for the tip.

---

### Post by kraftwerk-it on 2008-04-27
Burned a new CD at 4x speed. Reinstalled using Wubi. After reboot started Hardy, decided to grit my teeth and wait it out. The result? I've got Ubuntu 8.04 dual-booting sweetly with Vista!

---

### Post by GepettoBR on 2008-04-28
Congratulations!

---

### Post by Solrac924 on 2008-05-03
great job kraftwerk-it!

you can thank me by clicking on the medal :cool:

---


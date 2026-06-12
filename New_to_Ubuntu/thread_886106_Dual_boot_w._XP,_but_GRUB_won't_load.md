---
title: "Dual boot w. XP, but GRUB won't load"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by caffeineme on 2008-08-10
Hi all!

I'm trying to do a clean install of Hardy. I have XP installed, and boot from my CD. Install appears OK, and then I reboot, and always, I'm going right into XP. Attempting this on the same HDD (different partition), and I've also tried on a sep. hard drive. Tried the guided install, as well as manual partitioning. Each time, boots right back to XP. Any suggestions? Thanks!

Bill

---

### Post by Unstuck on 2008-08-10
can you post the contents of your menu.lst?

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Unstuck on 2008-08-10
I wonder if you've checked out [these]("http://ubuntuforums.org/showthread.php?t=179902") [posts]("https://help.ubuntu.com/community/WindowsDualBoot")?

Together, they helped me get my dual boot to work...and I suck at almost everything.

---

### Post by bobpur on 2008-08-10
You haven't mentioned what kind of drives you have (PATA or SATA). Your problem sounds typical of a PATA hdd that has the jumpers and/or cable placement screwed up.
The PATA cable is the 2" wide cable with three (usually) connectors on it. The connectors should be labelled in some way. By color or labeled on the cable. From tjhe motherboard end; the slave connector is the one in the middle and the master is the one on the far end from the moto.
The hdd's will have three jumper settings. 1). MA= master, 2). SL= slave, and 3). CS= cable select. 
Place the jumper for how you want the drive to function and connect to the proper connector for that jumper setting and you should be fine.
Also. if the Ribbon cable has any age at all to it, it wouldn't hurt to replace it with a new one. 

I hope that helps.

---


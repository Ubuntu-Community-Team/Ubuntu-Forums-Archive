---
title: "Unable to Spin Disks Down"
date: 2013-09-28
forum: New to Ubuntu
---

### Post by Robert_Adamson on 2013-09-28
Absolute newbie hence posting here.
New media server - ancient Via Epia board with SSD for OS and hard drive for media. Running Ubuntu 10.04.4 as this is the latest release which will run on a cpu without cmov.

Have installed the following - openssh-server, Samba, VNC, Logitech Mediaserver and run headless to a mixed OS network.

No big problems however I can't get the media drive to spin down. The processor is low power, fanless and will run 24/7 and I want to spin the hdd down when not actively serving.

I have tried "sudo hdparm -S120 /dev/sdb" which has no effect. The drive is always active/idle.
I notice that "sudo hdparm -Y /dev/sdb" spins the drive down but immediately crashes the system.

Any/all help much appreciated.

---

### Post by rubylaser on 2013-09-28
Are you sure that your OS isn't running off /dev/sdb?  Spinning down a disk unless it's the OS drive, should not cause a crash.  Also, your disk needs to support Advanced Power Management to be spun down with the -S flag.  I have a post that covers spinning down disks alongside SMART monitoring that covers all of this topic.

[http://zackreed.me/articles/60-spin-down-idle-hard-disks](http://zackreed.me/articles/60-spin-down-idle-hard-disks)

---

### Post by Robert_Adamson on 2013-09-28
> **rubylaser said:**
> your disk needs to support Advanced Power Management to be spun down with the -S flag.  

Got it in one! A different hdd solved the spin down problem thanks!
That's what comes of raking around in the junk box I guess.

> **rubylaser said:**
> Are you sure that your OS isn't running off /dev/sdb?  Spinning down a disk unless it's the OS drive, should not cause a crash.

Solved the other problem too that spinning down the drive makes the system reboot.
This turned out not to be a software problem at all but a hardware glitch.
It seems that my power supply glitches when the disk load is suddenly removed and this causes the bios to initiate a reboot.
(Tested this by running the CD to load the supply during a spindown and all went OK).

---


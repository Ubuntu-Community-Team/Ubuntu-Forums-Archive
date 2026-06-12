---
title: "[SOLVED] Building Ubuntu NAS, couple of questions"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by BassKozz on 2008-12-01
I have an old P4 3.0GHz laying around that I would like to turn into a NAS using Ubuntu 8.10 Desktop.  It has 4GB of RAM in it (more then enough), and I plan on running Samba Shares, FTP, and possibly Apache on it (for internal web-hosting).  

I've got two questions:[LIST=1]
[*]I plan on running a software RAID 5 (mdadm) on this machine, it has 2 ide ports available and 2 SATA ports.  I plan on running the OS on a single IDE drive (non-raid), and the RAID 5 will consist of 1x IDE drive and 2x SATA drives (I have 3x 300GB drives laying around, so that should make a 600GB RAID 5 with redundancy), **is it ok to mix IDE and SATA drives with software RAID (mdadm)?**

Also where is a good place to start when looking for info on how to setup a software raid using mdadm?


[*]**What sort of power-saving settings can I setup for my NAS so that it's not sucking down power 24/7?**
This box will be headless, so I already got that going for me (no monitor).  But I was wondering if there is a way to setup the NAS so that is spins-down or puts the computer sleep mode when it's not being accessed. I would hate to have the drives spinning 24/7 if they don't have to.[/LIST]


TiA,
-BassKozz

---

### Post by cozmicharlie on 2008-12-01
Software raid is very easy to set up on Ubuntu.  A few sources that might help you

This is a simple How To with screenshots.
[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

The software raid How To is getting a but old but the info is still good.
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)

Numerous articles on "How To Forge" that might help.
[http://www.howtoforge.com/trip_search](http://www.howtoforge.com/trip_search)

hope this helps

---

### Post by BassKozz on 2008-12-01
Thanks for the resources **cozmicharlie**,

Anyone know if there is a problem with me mixing SATA & IDE in a Software RAID Array?
Also any info on Power-Saving settings I might beable to use w/ Software RAID that will spin down disks when not in use?

---

### Post by anewguy on 2008-12-01
I hope this will answer your questions about mixed adapter RAID arrays:

[http://www.howinthetech.com/quick-and-dirty-linux-software-raid5/]("http://www.howinthetech.com/quick-and-dirty-linux-software-raid5/")

Dave :)

---

### Post by BassKozz on 2008-12-17
Thanks for all the help everryone, I am marking this thread [SOLVED] and I've moved the powersaving question here; [http://ubuntuforums.org/showthread.php?t=1012959](http://ubuntuforums.org/showthread.php?t=1012959)

---


---
title: "Setting permissions on USB drive using LIve CD"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by PrairieShaman on 2008-06-09
Hey folks.. here's my story.

I was running the 8.04 updater the other day and accidentally had the computer power down in the middle of installing them. 

Now when I boot I get a no image present or something error and my monitor goes to sleep mode, I cannot get to the GUI login and my keyboard doesnt work on the command line.. so I can still get my files booting with the live CD. So I went and got a 200GB External USB hard drive to copy my files to and was planning on just doing a fresh install of 8.04. But I cannot seem to get the USB drive to work properly to allow me to copy files to it.. 

I am using the live CD, keep in mind.

I formatted the drive as EXT3 and then tried EXT2  with the same problem. when copying files over it gives me the following error.. any help would be greatly appreciated.

ERROR:
The folder "documents" cannot be copied because you do not have permissions to create it in the destination.

Here is my fdisk results:
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d5a97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14338   115169953+  83  Linux
/dev/sda2           14339       14946     4883760    5  Extended
/dev/sda5           14339       14946     4883728+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e83eb1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24792   199141708+  83  Linux

---

### Post by miss.magenta on 2008-06-09
have you tried sudo chmod -R a+w /path/to/mountpoint?

---

### Post by PrairieShaman on 2008-06-09
Thank you!!!

---


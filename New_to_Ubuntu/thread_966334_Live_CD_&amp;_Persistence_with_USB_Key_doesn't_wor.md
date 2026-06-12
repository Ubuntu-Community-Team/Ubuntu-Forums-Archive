---
title: "Live CD &amp; Persistence with USB Key doesn't work"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by oOarthurOo on 2008-11-01
I've formatted a usb key to have two partitions, 1GB fat 32 and 1GB ext2. The ext2 partition is labelled "casper-rw" as per persistence instructions on Ubuntu docs. When I boot I press F6 to get other options, and add "persistent" to the end of the boot line. When I get to the desktop I install firefox, then reboot, add persistent again and firefox is missing.

In other words, persistence doesn't seem to be working.

I need skype and firefox to be available for use with the live cd.

---

### Post by C.S.Cameron on 2008-11-01
Type (space)persistent.
The ext3 casper-rw partition does not always work for me, but an ext3 home-rw does.

---

### Post by oOarthurOo on 2008-11-01
I'm not sure what worked, I reformated creating just one ext2 partition, named it home-rw and rebooted cafeful to do space persistent.

Some of my changes stuck, but the two apps I installed skype and firefox were gone upon reboot.

---

### Post by oOarthurOo on 2008-11-02
Just to clarify, persistence is working now however I'm not able to use persistence to actually do something useful, like install skype and have it available upon reboot using a live-cd and persistent USB. Is this even possible, or must I remaster a cd?

---

### Post by C.S.Cameron on 2008-11-02
I've noticed that when casper-rw shows up on the desktop it is not working, but when I boot and it doesn't show up persistence of downloaded files does work.
Not yet sure how to fix this.

---

### Post by oOarthurOo on 2008-11-02
Are you saying that you've installed a program and rebooted and it was available, at least some of the time?

---

### Post by C.S.Cameron on 2008-11-02
Yes.
Had it working for a while with the beta 8.10 CD.
Today with 8.10 final, I managed to write a bunch of files and folders to casper-rw, when downloading stuff, but they were not available on reboot.
They were still in the casper-rw partition.
Tried it with the Xubuntu 8.10 final CD also, that might have been when the stuff was written.
When I use this flash drive along with a Live USB Flash drive, (usb-creator), it works every time, 
It works as partitions on a Persistent flash drive also, (once I delete the casper-rw file U-C makes).
looking in gparted, when casper-rw shows up as being mounted /casper-rw, persistence seems to work.
when it shows up as being mounted /media/casper-rw, it does not.

---


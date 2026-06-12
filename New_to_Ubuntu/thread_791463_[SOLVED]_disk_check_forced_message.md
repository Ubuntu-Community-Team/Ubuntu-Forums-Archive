---
title: "[SOLVED] disk check forced message?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-12
I noticed that on boot the other day, I got the following message

[COLOR=Blue]Dev/sda3 mounted 28 times without being checked -- check forced
[/COLOR]
The system then did a sector scan I think, and then rebooted. This was the sort of process that system mechanic 7 pro in windows XP used to do to me, I thought it was because of the way vfat wrote to the hard drive, Obviously I am wrong.

Can someone tell me what the process is, why it is happening, and is it normal?

Thanks

---

### Post by philinux on 2008-05-12
It's normal every so many boots depending how big the partition is. I think mine got 36. good news is that in hardy it tells you the progress as before all we got was a black screen. Great improvement.

It's running fsck which is the ext3 file system check.

---

### Post by Thingymebob on 2008-05-12
For info
The system utility fsck (for "file system check" or "file system consistency check") is a tool for checking the consistency of a file system in the Unix system and clones thereof, such as AIX and Linux

Generally, fsck is run automatically at boot time when the system detects that a file system is in an inconsistent state, indicating a non-graceful shutdown, such as a crash or power loss. Typically, fsck utilities provide options for either interactively repairing damaged file systems (the user must decide how to fix specific problems), automatically deciding how to fix specific problems (so the user doesn't have to answer any questions), or reviewing the problems that need to be resolved on a file system without actually fixing them.

Fsck can also be run manually by the system administrator if there is believed to be a problem with the file system. However, running fsck on a mounted file system can potentially cause severe data corruption/loss.

A journaling file system is designed such that tools such as fsck do not need to be run as often. The UFS2 Filesystem in FreeBSD has background fsck, so it is usually not necessary to wait for fsck to finish before accessing the disk.

The Microsoft equivalent programs are scandisk and chkdsk.

journaling protects against a sudden power off, so it can rebuild the file system. Fsck just checks if the file system has been corrupted or is fragmented. Ext3 is pretty good at not getting fragmented but with ext4 and extents fragmentation will be a thing of the past.

---

### Post by drs305 on 2008-05-12
And further:

To set the interval between fsck checks
```
sudo tune2fs -c60 /dev/hda2
```
In this example, tune2fs would set fsck to check hda2 every 60 boots.

---

### Post by tropdoug on 2008-05-14
Thanks guys, 

another little bit of Linux knowledge tucked away. I read some of the posts here about this difficulty and that one, and then some who "spit the dummy" but never in all the years of computing that I have been doing, have I come across a group so willing and able to help as the community of Ubuntu does. 

I for one will be staying with Linux, and as I learn hopefully I will be able to contribute back to the community too. 

Guys have an excellent life wherever you are and whatever your circumstances. 

Douglas

---


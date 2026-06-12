---
title: "External Hard drive problems, and wireless help"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Sailorcancer on 2008-09-20
About a year ago I used Xubuntu *which did not go all that great* which saw my external HDD just fine.  For some reason Ubuntu just does not want to.  I have checked around and could not find how to fix my problem.  I did see that a lot of people asked the OP to do a: sudo fdisk -l  Here is what came from mine:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab89ab89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40dd40dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS
```

My desktop has two hard drives in it, which Ubuntu sees but for some reason it won't see my external.  It is powered on and plugged in.  BTW Ubuntu does see other USB devices I plug in like flash drives and my webcam.

My next problem is my wireless.  For some reason under Ubuntu I only get 50-70% signal strength, which is completely different from what I receive under XP *which is a lot higher*.  How can I make it higher?  drivers from my cards site does not handle Linux only Windows.  I have a TRENDnet TEW-443PI card.

---

### Post by bumanie on 2008-09-20
Will leave the wireless question to others.
As for the external hard drive, what filesystem are you running on it? Was it shutdown correcty. Are you getting any message when trying t mount it, if so, please post the error message.

---

### Post by Sailorcancer on 2008-09-20
No error messages, NTFS.

As for it being shut down correctly yes.  Windows see it just fine, and when I tried Xubuntu a year ago it saw it just fine.  I have turned the external HDD on and off and nothing happens.

---

### Post by Sailorcancer on 2008-09-20
Just bringing this up.

---


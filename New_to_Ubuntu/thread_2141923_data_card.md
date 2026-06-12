---
title: "data card"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by Anoop Jose on 2013-05-04
Hi,
 i have memory card of 4 GB. when i connect the same to windows system,  it tells to format the card to use. in ubuntu id doesnt shw. i ve  valuable data in that drive . how can i extract it?

when i use testdisk it comes like this.
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
 Disk /dev/sda - 250 GB / 232 GiB - Hitachi HDP725025GLA380
>Disk /dev/sdb - 32 MB / 30 MiB - Mass Storage Device








>[Proceed ]  [  Quit  ]

 wat to do next as its nt showing the exact size

---

### Post by AngJinhang on 2013-05-04
Well, it does not show the right size of your disk because the disk is broken! If you format it, you will lose all the data. So... I have a way, but it is not guaranteed to work. I have not tested it before.
1. Install gparted from the software center.
2. Fire it up from the dash, or the terminal. Give the system your password when prompted.
3. It should find your drive. But it may fail to find the filesystem of the disk.
4. Find a recover data button, or save data, backup, or whatever. (I'm not really sure whether this button exists or not)
Good luck!
Jinhang

---

### Post by Mark Phelps on 2013-05-04
I have never used GParted to do data recovery -- as my own experience has been that Windows data recovery apps do better on Windows filesystems, and Linux data recovery apps do better on Linux filesystems.

There is one Windows data recovery app (recuva) which is free, but you get what you pay for -- so it may not recover much.

---


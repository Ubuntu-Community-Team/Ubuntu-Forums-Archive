---
title: "Re-sizing partitions."
date: 2014-01-09
forum: New to Ubuntu
---

### Post by wzissel on 2014-01-09
I just got Ubuntu and went to install steam games and I did not have enough disk space. I am positive I have free disk space (over 200GB) so it must be that the
 partition is out of space. Which partitions should I shrink, increase, and so on...? I cannot identify which one is for Ubuntu and the others that are for Windows (they are installed alongside eachother). I installed Ubuntu using Wubi. Any help would be appreciated.
Screenshot of partitions:
[ATTACH=CONFIG]249346[/ATTACH]

---

### Post by zircon_34 on 2014-01-10
Windows is probably on sda1, but your partition scheme seems weird to me. The partition format for Ubuntu should be ext4 not ntfs...right? and you have no SWAP  partition. did you change the default partition scheme from your Ubuntu installation?

you should have 3 partitions for Ubuntu:
/ (rootfilesystem)
swap (around 4Gb) 
/home (optional, is like your user folder)

Here are some screenshots you may use as reference. 
[http://linux-shift.com/2012/05/22/creating-separate-home-partition-ubuntu-1204/](http://linux-shift.com/2012/05/22/creating-separate-home-partition-ubuntu-1204/)

---

### Post by Impavidus on 2014-01-10
This is normal for wubi installations. /dev/sda1 is a Windows boot partition, /dev/sda2 is the main Windows partition, /dev/sda3 is the Windows recovery partition and /dev/sda4 has some HP tools which you'll probably never need. There is no Linux partition, as in Wubi installations Ubuntu is installed on a virtual partition, which is just a file on your main Windows partition. So you did not install Ubuntu alongside Windows, but more like half alongside/half inside Windows (not really inside, as that would be a virtual machine).

It is possible to resize wubi installations: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk). The maximum is about 30GB. Wubi is being phased out, so the latest releases of Ubuntu are not supported as wubi and support for 12.04 is not as good af for true dual boots. Using wubi is no longer recommended.

You can install as a true dual boot, for which you have to boot from a live dvd or usb. There is one complication. You can have at most 4 primary partitions on your drive, so you cannot add the Linux partitions you need. You could, for example, create a backup of /dev/sda4 on a dvd, defrag and shrink /dev/sda2, delete /dev/sda4 and boot from the live disk. The installer should see the unallocated space on your drive and install in some logical partitions there.

---


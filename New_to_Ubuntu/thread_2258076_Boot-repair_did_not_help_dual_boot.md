---
title: "Boot-repair did not help dual boot"
date: 2014-12-24
forum: New to Ubuntu
---

### Post by varma99 on 2014-12-24
Dual boot did not work upon successful installation of Ubuntu 14.0.4 on a windows 7 system. 
Followed  'boot-repair'  instructions specified [here]("https://help.ubuntu.com/community/Boot-Repair"). 
'Boot-Repair' ran successfully with the log [http://paste.ubuntu.com/9612181](http://paste.ubuntu.com/9612181)
Upon rebooting, the system did not given an option to choose Windows or Ubuntu but now defaulted to Ubuntu.
Can you pls suggest how to fix it?

---

### Post by oldfred on 2014-12-24
You have these two entries at the end of your grub menu, do they not work?

 Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2

You also installed grub2 to the partition boot sector of sda5, which with grub2 is not recommended as it is forced to use blocklists.
And you have the very old grub4dos (/grldr) to chain load. That usually is from EasyBCD.
Unless not really using Ubuntu I would suggest to remove EasyBCD as grub usually works better.

---

### Post by Sef on 2014-12-26
[SuperGrubDisk]("http://www.supergrubdisk.org/") works really well.

---


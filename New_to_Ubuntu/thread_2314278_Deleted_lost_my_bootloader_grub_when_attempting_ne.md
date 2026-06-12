---
title: "Deleted/ lost my bootloader/ grub when attempting new install of 14.04.4 LTS"
date: 2016-02-19
forum: New to Ubuntu
---

### Post by ubuntark on 2016-02-19
I erased or lost my bootloader/ grub when attempting new install of 14.04.4 LTS.

During the install I recieved a message that the bootloader was unable to be to install and I would need to do it manually.

What steps do I take to attempt to get my system to a workable condition?

Currently I can only test/try the basic ubuntu system temp OS from an old 15.04 disk or from the bootable USB I created for the newer 14.04.4 install. 




Thanks in advance for you help and time.


_______________
Not a dual boot system.
Only need ubuntu on this custom laptop:
Memory 15.6 GiB
Processor Intel Core i7-4700MQ CPU @ 2.40GHz x 8
Graphics Intel Haswell Mobile
OS 64 -bit
Disk 8.4 GB

---

### Post by grahammechanical on 2016-02-19
> Disk 8.4 GB

I cannot believe that your hard disk is only 8.4 DB in size. If there is only one hard drive then Linux will see it as sda. So, load a Ubuntu live session and use the File Manager to access the hard drive. That will mount the hard drive. Then open a terminal and run these two commands

```
grub-install /dev/sda
update-grub
```

I do not think that you need to prefix either command with sudo.

Regards.

---

### Post by sisco311 on 2016-02-19
You can try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") to fix your problem. If that doesn't work, then please post your [Boot Info]("https://help.ubuntu.com/community/Boot-Info") .

---


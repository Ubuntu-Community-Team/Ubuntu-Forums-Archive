---
title: "USB 1GB pen drive does not work"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by SauPa on 2012-06-02
When I connect my Pen drive to ubuntu, nothing happens. ( the usb pen drive itself is fine)

  How can I access the files on my USB drive ?  
  Will I have to install a driver for this ?
  Is this a matter of changing the System Settings ?
  Why cannot I see the external drive somewhere ? ( I am a absolutely new to ubuntu, so if there is a command or option please tell me)

thanking you in anticipation

Saupa

Ouput of Commands lsusb and  fdisk

:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0402:7675 ALi Corp. 
Bus 001 Device 006: ID 1e3d:2092  



:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b61c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   306440191   153219072   83  Linux
/dev/sda2       306442238   312580095     3068929    5  Extended
/dev/sda5       306442240   312580095     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 1058 MB, 1058537472 bytes
2 heads, 63 sectors/track, 16408 cylinders, total 2067456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00357c8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     2067455     1033712    6  FAT16

---

### Post by dcsoldschool53 on 2012-06-02
When you type in a terminal```
ls /media
```what do you see? Also when you click "Places" on the gnome panel, do you see your pen drive in the drop down list?

---

### Post by inashdeen on 2012-06-02
you are confirm that the pendrive is fine? as far as i know all pendrive is plug and play. if i am not mistaken

---


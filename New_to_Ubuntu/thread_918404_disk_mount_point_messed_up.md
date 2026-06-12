---
title: "disk mount point messed up"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by cooljeff3000 on 2008-09-12
simple leetle problem, I was fiddling around with VLC, trying to get a disk to play and somehow /dev/hda dissapeared! anyway so i had to keep changing the disk play point for VLC to /media/[name of disk] after a bit that got annoying (especially since star trek STILL wouldn't play(scrubs worked fine though)) so i changed the mount point of the disk drive to /dev/hda but now when i try and mount it I get an error message saying "mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)" HOW DO I CHANGE THE MOUNT POINT BACK??? (and if you could help me with the other stuff that's be fine)

---

### Post by iaculallad on 2008-09-12
Post whatever displays when you issue this terminal commands:

```
cat /etc/fstab
sudo fdisk -l
sudo blkid

```

---

### Post by cooljeff3000 on 2008-09-12
root@HackPack:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=be8c9b5a-e770-4c01-acd5-6d0e6f4e65ca /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=435a139a-ce4e-4858-b717-320b1325014c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
root@HackPack:~# sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd969d969

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19883   159710166   83  Linux
/dev/sda2           19884       20023     1124550    5  Extended
/dev/sda5           19884       20023     1124518+  82  Linux swap / Solaris
root@HackPack:~# sudo blkid
/dev/sda1: UUID="be8c9b5a-e770-4c01-acd5-6d0e6f4e65ca" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="435a139a-ce4e-4858-b717-320b1325014c"
root@HackPack:~#

---

### Post by iaculallad on 2008-09-12
Post can't give us any hint for now. Try posting what this command displays:

```
dmesg |grep hda
```

---

### Post by cooljeff3000 on 2008-09-12
jeffrey@HackPack:~$ dmesg |grep hda
[   40.284843] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
jeffrey@HackPack:~$

---

### Post by elastigirl on 2008-10-01
Hi Cooljeff, I have the same problem :(. Did you manage to fix this? Please do let me know if you did, would appreciate it.

---


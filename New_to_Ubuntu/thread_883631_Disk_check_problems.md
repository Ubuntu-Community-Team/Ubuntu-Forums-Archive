---
title: "Disk check problems"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-08-08
so i posted this before but i didnt check it anymore and mcduck told me to run some commands  > **mcduck said:**
> Could you run the following commands in temrinal and post the outputs here so we can take a look at your disk configuration:

"sudo fdisk -l"

"blkid"

"cat /etc/fstab"

..and no, you shouldn't reinstall Ubuntu. Most of the problems in Linux can be fixed without reinstallin, it's not Windows, you know.. ;)

(you can copy & paste to/froma  terminal by selecting the text you want to copy and the pressing the middle mouse button (the wheel) where you wish to paste. Or with Shift-Ctrl-C and Shift-Ctrl-V, if you like)


















so heres my output





sudo fdisk -l
-------------------------------------------------------------------------

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11330    91008193+   7  HPFS/NTFS
/dev/sda2           47495       48641     9213277+   7  HPFS/NTFS
/dev/sda3           11331       47494   290487330    5  Extended
/dev/sda5           11331       46406   281747938+  83  Linux
/dev/sda6           46407       47494     8739328+  82  Linux swap / Solaris

Partition table entries are not in disk order


blkid-nothing happens
----------------------------------------------------------------------------


cat/etc/fstab



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=cc52bdea-2d00-4e13-a754-30e7b426d97c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b36bf569-d4a9-4d90-87ed-ff8a49b65581 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by ajgreeny on 2008-08-08
It needs to be ```
sudo blkid
```for that command so try that again, post the output here, and let's see what that tells us.  It may be that fsck is trying to check a partition but that partition can not be detected properly, as the fstab has the wrong UUID.

---

### Post by mcduck on 2008-08-08
> **ajgreeny said:**
> It needs to be ```
sudo blkid
```for that command so try that again, post the output here, and let's see what that tells us.  It may be that fsck is trying to check a partition but that partition can not be detected properly, as the fstab has the wrong UUID.

No, blkid shouldn't need admin privileges.

BUt there seems to be a bug where on some systems it, for some reason other other, needs them: [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/220275]("https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/220275"). So if you get no results with "blkid" try with sudo. Or run "ls -la /dev/disk/by-uuid" which should also print UUID's for your partitions.

---

### Post by ajgreeny on 2008-08-08
Thanks mcduck, I wasn't aware of this bug, and certainly on my system blkid gives empty output and needs sudo, though the folder /dev/mapper permissions allows access to all, owned by root, of course.

---

### Post by mr-Kirch on 2008-08-11
k sorry i havnt replyd (havnt used ubuntu for like 3 days now)

heres my output for sudo blkid


/dev/sda1: UUID="FAE8B084E8B040A5" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="Recovery" TYPE="ntfs" 
/dev/sda5: UUID="cc52bdea-2d00-4e13-a754-30e7b426d97c" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="b36bf569-d4a9-4d90-87ed-ff8a49b65581"

---


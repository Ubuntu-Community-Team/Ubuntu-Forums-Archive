---
title: "Installing 8.04 - Fat directories not mounted"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by David1000 on 2008-05-03
I have installed Ubuntu 8.04 and my FAT directories were not mounted; and there is no entry for them n fstab.

I notice that the mount instructions for ext3 directories differ a little from 7.10 so presumably, vFat will also.

In 7.10, an example of my fstab entry is:
# /dev/hdb8
UUID=334E-29B0  /media/hdb8   vfat  defaults,utf8,umask=007,gid=46 0       1
/dev/hdb8    /home/david/zBackup/Original-Photos  vfat  defaults,utf8,umask=007,gid=46 0       1

What would it be now?  (I have the current UUIDs).

---

### Post by Patb on 2008-05-03
David, someone should be able to quickly help if you post the output of 
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```Please do that (ie from your 8.10 install).  

Cheers, Pat.

---

### Post by David1000 on 2008-05-03
Got it all figured out.  The problem originally stemmed from not specifying a mount point for my fat32 directories when installing linux.  Did that on a reinstall and now all OK.

---


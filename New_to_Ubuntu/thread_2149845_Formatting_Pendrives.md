---
title: "Formatting Pendrives"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by Apii on 2013-05-30
Please how do I use Ubuntu terminal to format a pendrive

---

### Post by lethall1 on 2013-05-30
[http://linux.die.net/man/8/fdisk](http://linux.die.net/man/8/fdisk)
[http://linux.die.net/man/8/mkfs](http://linux.die.net/man/8/mkfs)

whith fdisk you must create new partition if there is no, with mkfs.(ntfs) create new file system. Then use mount command.

---

### Post by Paqman on 2013-05-30
Does it have to be through the terminal? If not you can use the preinstalled tool called Disk Utility. Just click on the drive and hit the "format" button.

---

### Post by slickymaster on 2013-05-30
> **Paqman said:**
> Does it have to be through the terminal? If not you can use the preinstalled tool called Disk Utility. Just click on the drive and hit the "format" button.

+1

But if you really want to do it through the terminal, first of all you need to know the name of your pen drive or memory cardtype. For that use the following command:```
dmesg | tail
```It will show something like this (this is my output, yours could be diferent):```
~$ dmesg | tail
[ 7271.588923] sd 3:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 7271.598479] sd 3:0:0:0: [sdb] No Caching mode page present
[ 7271.598490] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 7271.657575] sd 3:0:0:0: [sdb] No Caching mode page present
[ 7271.657592] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[COLOR=#ff0000][ 7271.665830]  sdb: sdb1[/COLOR]
[ 7271.712364] sd 3:0:0:0: [sdb] No Caching mode page present
[ 7271.712378] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 7271.712387] sd 3:0:0:0: [sdb] Attached SCSI removable disk
```Then unmount your pen drive using the following command:```
sudo umount /dev/sdb1
```After that enter the following command to format your pen drive with FAT32 partition:```
sudo mkfs.vfat -n 'label_name' -I /dev/sdb1
```If you want to format it to ext4, then the command to run has to be:```
sudo mkfs.ext4 -n 'label_name' -I /dev/sdb1
```

---


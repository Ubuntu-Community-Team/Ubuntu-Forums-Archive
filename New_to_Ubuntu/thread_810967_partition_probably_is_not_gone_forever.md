---
title: "partition probably is not gone forever"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-05-28
Related to:  [http://ubuntuforums.org/showthread.php?t=810826](http://ubuntuforums.org/showthread.php?t=810826)
I installed ubuntu and had it use my data partition mount to /media/datadisk now I just changed fstab to have that partition mount to /mnt/datadisk.  On restart it is not loading the partition at all.  There is still a folder in /media called datadisk with no data and there is nothing under the /mnt folder.  Here are my fstabs, any ideas on what went wrong?
Current:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=ecf7e2b0-b455-403e-8797-ab93639735c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda2
UUID=b3b801c3-3c82-440a-ac2a-1d1cb4f51c94 /mnt/datadisk ext2    relatime        0       2
# /dev/hda6
UUID=5ffba8b3-9e9f-40d3-b226-34e44a7de4b0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
Old:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=ecf7e2b0-b455-403e-8797-ab93639735c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda2
UUID=b3b801c3-3c82-440a-ac2a-1d1cb4f51c94 /media/datadisk ext2    relatime        0       2
# /dev/hda6
UUID=5ffba8b3-9e9f-40d3-b226-34e44a7de4b0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by bwhite82 on 2008-05-28
In order to mount something somewhere, you *usually* must create the directory first:

sudo mkdir /mnt/datadisk

---

### Post by fontenot_1031 on 2008-05-28
it's probably also worth mentioning that under /dev/disk/by-uuid most of the links there have the broken symbol on them (except for the link to my CD Drive) (as well as under by-id and by-path.

---

### Post by fontenot_1031 on 2008-05-28
ok the seperate partition mounts on boot.  Thanks man.  Now I just need to find out how to get the separate drive to show up on the desktop.

---

### Post by bwhite82 on 2008-05-28
> **fontenot_1031 said:**
> ok the seperate partition mounts on boot.  Thanks man.  Now I just need to find out how to get the separate drive to show up on the desktop.

I believe that is an option in gconf-editor, I cannot however, remember exactly where.

---


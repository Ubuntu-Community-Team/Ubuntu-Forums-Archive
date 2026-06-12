---
title: "[SOLVED] Partition not mounting on startup."
date: 2008-05-30
forum: New to Ubuntu
---

### Post by rabidninjawombat on 2008-05-30
Title explains it.. every time i reboot i have to manually remount the partition that i want auto mounting. (the one i set to mount to /mnt/multimedia.  I have already created the folder in the /mnt directory 

Here is my /etc/fstab , its the last one on the list..i think everything is set up properly. If you have any suggestions it would be appreciated. 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=f52792a5-0355-4ae2-b53c-0cc12d7d3a77 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=604144a8-65b7-44e2-9150-43c209f1f493 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /mnt/multimedia  ext3   default,devgid=100   0   0
```

---

### Post by wolfen69 on 2008-05-30
```
/dev/sda1       /mnt/multimedia  ext3   default,devgid=100   0   0
```
try changing to this
```
/dev/sda1       /mnt/multimedia  ext3  user,rw,exec,auto  0  0 
```
dont forget to put your cursor at the end of the last line and hit enter to create a new line without anything on it. then save. 
and backup your fstab first.

---

### Post by rabidninjawombat on 2008-05-30
> **wolfen69 said:**
> ```
/dev/sda1       /mnt/multimedia  ext3   default,devgid=100   0   0
```
try changing to this
```
/dev/sda1       /mnt/multimedia  ext3  user,rw,exec,auto  0  0 
```
dont forget to put your cursor at the end of the last line and hit enter to create a new line without anything on it. then save. 
and backup your fstab first.

will change it. 

I was always under the impression that the "default" command included the "user, rw, exec, auto" commands.

---

### Post by rabidninjawombat on 2008-05-30
hrrmm that appears to have fixed it.. im happy with that :)

---


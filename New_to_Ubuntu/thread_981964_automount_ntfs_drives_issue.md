---
title: "automount ntfs drives issue"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by gaffurabi on 2008-11-14
i tried to add uuid numbers to my fstab and it looks like this (i use ubuntu 8.10):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2f22f78a-79ef-47e3-a053-9e5289758525 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2b180a47-4441-42a9-9183-ca5f63db4fb5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=FECC0E85CC0E3883 /media/backup ntfs defaults,umask=007,gid=46 0 0  
UUID=3A6832B56832702D /media/backup ntfs defaults,umask=007,gid=46 0 0 
UUID=84944B06944AF9E6 /media/backup ntfs defaults,umask=007,gid=46 0 0 
UUID=2C3056FB3056CB88 /media/backup ntfs defaults,umask=007,gid=46 0 0 
UUID=26605BB3605B8907 /media/backup ntfs defaults,umask=007,gid=46 0 0 
```

now ubuntu mounts only one drive (even if i click on others) which is /dev/sdb6: UUID="26605BB3605B8907" LABEL="PRIVAT" TYPE="ntfs" 
where did it all go wrong?

---

### Post by taurus on 2008-11-14
You use the same mount point, /media/backup, for all of your ntfs partitions so that's why the last one will only show up!  Try using different mount point for different partition, okay.

---

### Post by pluckypigeon on 2008-11-14
here is a post about automounting and editing fstab:

[http://ubuntuforums.org/showthread.php?p=6177625#post6177625](http://ubuntuforums.org/showthread.php?p=6177625#post6177625)

---


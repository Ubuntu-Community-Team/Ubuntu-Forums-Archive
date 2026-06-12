---
title: "Harddrive problems and wine problems"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by AsaguroiKishi on 2008-04-24
I'm trying to see the files on two of my hard drives. I have a small 4 gig hard drive for linux and apps, another for windows and apps and a 160 gig for my games, music, etc. I can't see any files on my windows or 160 gig, and to fully convert to linux i need to see those files. 

when i "cat /etc/fstab" this came up:

```
jack@Spade:/$ cat etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=1cef2263-9ab6-44f3-b9f5-c625e945dec3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=2c692c6c-ebd3-4045-8856-ce44a879140a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1       /mnt/jacksfiles ntfs ro,nls=utf8,umask=0222 0 0
```

Also, i'm trying to get wine but it says it won't download because I'm "holding a broken package".

---

### Post by Bodsda on 2008-04-24
run fstab as root

```
sudo cat /etc/fstab
```

---

### Post by AsaguroiKishi on 2008-04-24
jack@Spade:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=1cef2263-9ab6-44f3-b9f5-c625e945dec3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=2c692c6c-ebd3-4045-8856-ce44a879140a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1       /mnt/jacksfiles ntfs ro,nls=utf8,umask=0222 0 0jack@Spade:~$

---

### Post by AsaguroiKishi on 2008-04-24
*bump*

---

### Post by AsaguroiKishi on 2008-04-30
*bump*

---


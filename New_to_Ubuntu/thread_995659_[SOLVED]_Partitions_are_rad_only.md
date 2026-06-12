---
title: "[SOLVED] Partitions are rad only"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-11-28
Hi

I installed windows and then Ubuntu.

My partitions were initially NTFS. Later using Gparted I change them to EXT3.

But now all my partitions are read-only. Not sure its because of the way i partitioned.

When I mounted partition using mount -w the partition becomes read-write. But when it gets mounted during bootup it gets read-only.

In fstab I have

/dev/sda5 /media/disk1 ext3 default 0 0

---

### Post by hyper_ch on 2008-11-28
I think you just might not have set permissions correctly.

```

ls -al /media

```

---

### Post by Guruprasad on 2008-11-28
output

> guru@gurupc:~$ ls -al /media
total 36
drwxr-xr-x  9 root root 4096 2008-11-28 12:20 .
drwxr-xr-x 21 root root 4096 2008-11-05 00:11 ..
lrwxrwxrwx  1 root  999    6 2008-11-04 18:27 cdrom -> cdrom0
drwxr-xr-x  2 root  999 4096 2008-11-04 18:27 cdrom0
drwxr-xr-x  3 root root 4096 2008-11-26 17:31 disk1
drwxr-xr-x  3 root root 4096 2008-11-26 17:31 disk2
drwxr-xr-x  3 root root 4096 2008-11-26 17:26 disk3
drwxr-xr-x  3 root root 4096 2008-11-26 17:29 disk4
drwxr-xr-x  2 root root 4096 2008-11-28 11:22 disk5
lrwxrwxrwx  1 root  999    7 2008-11-04 18:27 floppy -> floppy0
drwxr-xr-x  2 root  999 4096 2008-11-04 18:27 floppy0
-rw-r--r--  1 root root    0 2008-11-28 12:20 .hal-mtab


---

### Post by Guruprasad on 2008-11-28
fstab file

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/sda5	/media/disk1	ext3	rw,user,auto	0	0
/dev/sda6	/media/disk2	ext3	defaults	0	0
/dev/sda7	/media/disk3	ext3	defaults	0	0
/dev/sda8	/media/disk4	ext3	defaults	0	0

# /dev/sda9
# UUID=f521b228-61c7-43cb-85ce-fb2f6d04f27c /       ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
#UUID=c7b6f3ad-05fa-4411-b54a-e14cb0193124 none            swap    sw              0       0
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by hyper_ch on 2008-11-28
well, if you see, the mounted partitions are owned by root and you only have read/write access....

run
```

sudo chown -R USERNAME.USERNAME /media/disk1

```

where USERNAME is your actual username.

---

### Post by Guruprasad on 2008-11-28
Thanks al lot..

Problem solved...

---


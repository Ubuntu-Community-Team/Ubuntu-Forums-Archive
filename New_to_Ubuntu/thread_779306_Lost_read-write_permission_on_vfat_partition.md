---
title: "Lost read-write permission on vfat partition"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Little Blue on 2008-05-02
Hi,

I boot ubuntu from an external harddrive, also on this HD is a vfat partition that I've been able to use freely since I installed.

However, this evening, it no longer seems to have read-write permission any more. (More specifically, after startup, it works for a few minutes and then locks my ability to write to it.)

I noticed that my torrent client gives an input/output error just as it loses the write permissions...

Looking at some similar threads, I hope the following info will be useful:
/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=9604ac6f-6fa7-4176-a5a4-255668559d85 /               ext3    defaults,errors=remount-ro 0       1
[b]# /dev/sdb1
UUID=17F5-3047  /ext01          vfat    defaults,utf8,umask=007,gid=46 0       0[/b]
# /dev/sda1
#UUID=16D9-B5D2  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda2
UUID=E538-CDE5  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda3
UUID=1733-AEBB  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sdb5
UUID=87305106-3a3c-4183-8ef7-c9284445dc55 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

fdisk -l
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x375a8313

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        6367    46026225    c  W95 FAT32 (LBA)
/dev/sda3            6368       12161    46540305    c  W95 FAT32 (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdb858cf

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1       54722   439554433+   c  W95 FAT32 (LBA)**
/dev/sdb2   *       54845       60801    47849602+  83  Linux
/dev/sdb3           54723       54844      979965    5  Extended
/dev/sdb5           54723       54844      979933+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

ls -la /
```

total 196
drwxr-xr-x  22 root root     4096 2008-02-24 21:54 .
drwxr-xr-x  22 root root     4096 2008-02-24 21:54 ..
drwxr-xr-x   2 root root     4096 2008-04-13 13:37 bin
drwxr-xr-x   3 root root     4096 2008-02-28 22:49 boot
lrwxrwxrwx   1 root root       11 2008-02-24 21:34 cdrom -> media/cdrom
drwxr-xr-x  14 root root    14200 2008-05-02 21:42 dev
drwxr-xr-x 119 root root    12288 2008-05-02 21:42 etc
**drwxrwx---  17 root plugdev 98304 1970-01-01 01:00 ext01**
drwxr-xr-x   3 root root     4096 2008-02-24 21:49 home
drwxr-xr-x   2 root root     4096 2007-10-16 00:17 initrd
lrwxrwxrwx   1 root root       33 2008-02-24 21:54 initrd.img -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  17 root root    12288 2008-04-13 13:37 lib
drwx------   2 root root    16384 2008-02-24 21:34 lost+found
drwxr-xr-x   6 root root     4096 2008-05-02 21:42 media
drwxr-xr-x   2 root root     4096 2007-10-08 11:47 mnt
drwxr-xr-x   2 root root     4096 2007-10-16 00:17 opt
dr-xr-xr-x 136 root root        0 2008-05-02 22:42 proc
drwxr-xr-x  16 root root     4096 2008-05-02 21:41 root
drwxr-xr-x   2 root root     4096 2008-02-28 22:49 sbin
drwxr-xr-x   2 root root     4096 2007-10-16 00:17 srv
drwxr-xr-x  12 root root        0 2008-05-02 22:42 sys
drwxrwxrwt  11 root root     4096 2008-05-02 21:47 tmp
drwxr-xr-x  12 root root     4096 2008-02-26 20:53 usr
drwxr-xr-x  15 root root     4096 2007-10-16 00:31 var
lrwxrwxrwx   1 root root       30 2008-02-24 21:54 vmlinuz -> boot/vmlinuz-2.6.22-14-generic

```

Any help would be greatly appreciated...

---


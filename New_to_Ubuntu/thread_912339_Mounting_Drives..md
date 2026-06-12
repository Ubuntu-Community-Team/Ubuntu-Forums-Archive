---
title: "Mounting Drives."
date: 2008-09-06
forum: New to Ubuntu
---

### Post by `Jon on 2008-09-06
I've just switched from Ubuntu to Xubuntu, and I have a problem. None of my HDDs are showing, except for the file system drive. Both of my other HDDs are showing in the BIOS, so I have no idea why I can't locate them...

---

### Post by hyper_ch on 2008-09-06
what's the output of

```

sudo fdisk -l

```

```

df -l

```

```

cat /etc/fstab

```

---

### Post by `Jon on 2008-09-06
jon@jon:~$ sudo fdisk -l
[sudo] password for jon: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9098cb58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9547    76686246   83  Linux
/dev/sda2            9548        9729     1461915    5  Extended
/dev/sda5            9548        9729     1461883+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93fd93fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19456   156280288+  8e  Linux LVM

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x446a4469

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19456   156280288+  8e  Linux LVM
jon@jon:~$ 

jon@jon:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76081180   1968728  70278140   3% /
varrun                  249596       100    249496   1% /var/run
varlock                 249596         0    249596   0% /var/lock
udev                    249596        60    249536   1% /dev
devshm                  249596         0    249596   0% /dev/shm
lrm                     249596     38684    210912  16% /lib/modules/2.6.24-19-generic/volatile
jon@jon:~$ 

jon@jon:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1dc8e8ef-8e75-4d06-a6ec-b06a81d35c76 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=415efef4-5efe-4e12-8c86-fd2a79dae4d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
jon@jon:~$

---

### Post by hyper_ch on 2008-09-06
put each output into [noparse]```

```[/noparse] brackets, so that it can be easier to read... run those commands again.

---

### Post by `Jon on 2008-09-06
Heh, sorry.


```
jon@jon:~$ sudo fdisk -l
[sudo] password for jon:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9098cb58

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9547 76686246 83 Linux
/dev/sda2 9548 9729 1461915 5 Extended
/dev/sda5 9548 9729 1461883+ 82 Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93fd93fd

Device Boot Start End Blocks Id System
/dev/sdb1 1 19456 156280288+ 8e Linux LVM

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x446a4469

Device Boot Start End Blocks Id System
/dev/sdc1 1 19456 156280288+ 8e Linux LVM
jon@jon:~$

```

```
jon@jon:~$ df -l
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/sda1 76081180 1968728 70278140 3% /
varrun 249596 100 249496 1% /var/run
varlock 249596 0 249596 0% /var/lock
udev 249596 60 249536 1% /dev
devshm 249596 0 249596 0% /dev/shm
lrm 249596 38684 210912 16% /lib/modules/2.6.24-19-generic/volatile
jon@jon:~$ 
```

```
jon@jon:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=1dc8e8ef-8e75-4d06-a6ec-b06a81d35c76 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=415efef4-5efe-4e12-8c86-fd2a79dae4d7 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
jon@jon:~$ 
```

---

### Post by hyper_ch on 2008-09-06
oh, it's lvm... I have no clue about that....

maybe there's a lvm manager gui tool... you'll need to find out how to mount LVM drives.

---


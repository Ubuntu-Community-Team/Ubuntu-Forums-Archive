---
title: "fresh hardy install: partitions show up in 'places' but not nautilus?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by snuffy on 2008-07-27
fresh install of hardy: partitions show up in 'places' but not in nautilus.

they then appear both on the desktop and in nautilus only once i click on the drive in 'places' 

is this a bug?  or do i need to do something to make them show up? 

cheers
tim.

---

### Post by ibuclaw on 2008-07-27
It isn't a bug, the drives are just not set to automount at startup , that is all.

It is easy to get it set up. Can you open up a terminal and post the output of these commands:
```
sudo fdisk -l
```
```
cat /etc/fstab
```

Regards
Iain

---

### Post by snuffy on 2008-07-27
its funny, because in the previous installation they automounted without me doing anything.



```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf22dbf81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4840    38877268+   7  HPFS/NTFS
/dev/sda2            4841        9726    39246795    f  W95 Ext'd (LBA)
/dev/sda5            4841        9726    39246763+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96a096a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+  83  Linux
/dev/sdb2           24079       24321     1951897+  82  Linux swap / Solaris
/dev/sdb3            2433       24078   173871495   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x15b40356

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      387621   195360952+   c  W95 FAT32 (LBA)
snuffy@snuffy-desktop:~$ 
```



```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=872a4f31-6c52-4d43-99cb-f478ffea78e8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=4567142f-63fe-4746-8502-0d4fe2e1c445 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
snuffy@snuffy-desktop:~$ 
snuffy@snuffy-desktop:~$ 
```

---

### Post by ibuclaw on 2008-07-27
Ok, for each of these devices, make a note of their UUID numbers.
```
sudo blkid /dev/sda1

sudo blkid /dev/sda5

sudo blkid /dev/sdb3

sudo blkid /dev/sdc1

```
For each, you will get an ouput like this:
[PHP]/dev/sda1: UUID="4DD33F1F16FC309A" TYPE="ntfs"[/PHP]
Just take a note of the UUID number, and **don't** include the " " double quotes. ( ie: 4DD33F1F16FC309A )

Then open up the fstab file.
```
sudo gedit /etc/fstab
```
And put this in at the bottom, then when you next reboot, it should mount all drives.
```

# sda1
UUID=**UUIDNUMBERHERE**    /media/sda1    ntfs    defaults,umask=007,gid=46,noatime    0    0
# sda5
UUID=**UUIDNUMBERHERE**    /media/sda5    ntfs    defaults,umask=007,gid=46,noatime    0    0
# sdb3
UUID=**UUIDNUMBERHERE**    /media/sdb3    ext3    relatime    0    2
# sdc1
UUID=**UUIDNUMBERHERE**    /media/sdc1    ntfs    defaults,umask=007,gid=46,noatime    0    0

```
Replace "UUIDNUMBERHERE" with the UUIDs of the drives that should be displayed from the above command.

Regards
Iain

---


---
title: "[SOLVED] NTFS partition mounting at 1st boot,not mounting at 2nd,mounting at 3rd and"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by IGITIHI on 2008-09-05
First of all, excuse me if this problem has been reported before but I could only find similar cases but not exactly the same.

I have used storage device manager and initially managed to mount all ntfs partition at boot time. However, one hard disk drive has two ntfs partitions. The first one always mounts normally but the second sometimes does not. After many reboot attempts, I found out that exactly **every second time I reboot the system, the second partition does not mount** and I can't even mount it manually because I get a message that I don't have permission to do so.

Any help will be appreciated!

---

### Post by iaculallad on 2008-09-05
You could try posting whatever displays when issuing this terminal commands so we could help you sort it out:

```
sudo blkid
sudo fdisk -l
cat /etc/fstab
```

---

### Post by alienexplorers on 2008-09-05
Read this it may help:
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by IGITIHI on 2008-09-05
```
igitihi@igitihi-desktop:~$ sudo blkid
[sudo] password for igitihi: 
/dev/sdc5: UUID="D258CF2B58CF0CE3" LABEL="MP31" TYPE="ntfs" 
/dev/sdc6: UUID="3610B93D10B90541" LABEL="MP32" TYPE="ntfs" 
/dev/sda1: UUID="8C4468124467FD78" LABEL="XP" TYPE="ntfs" 
/dev/sdb5: UUID="BE4C07D64C07887B" LABEL="Apps" TYPE="ntfs" 
/dev/sdb6: UUID="E6340DDC340DB09B" LABEL="Data1" TYPE="ntfs" 
/dev/sdb7: UUID="CE9C15A69C158A5B" LABEL="Data2" TYPE="ntfs" 
/dev/sda2: UUID="0be9c550-b9af-41ad-a7c9-e73af43578e5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="138d09af-217f-45d3-9b8b-b43dd183a30c" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="5e8eaf6d-4716-4e6e-9a5a-3271b485540f" 
igitihi@igitihi-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3240323f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5482    44034133+   7  HPFS/NTFS
/dev/sda2            5483        5495      104422+  83  Linux
/dev/sda3            5496        9507    32226390   83  Linux
/dev/sda4            9508        9729     1783215   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31973196

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2        8926    71690031    7  HPFS/NTFS
/dev/sdb6            8927       34864   208346953+   7  HPFS/NTFS
/dev/sdb7           34865       60801   208338921    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa1cf21a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdc5               2       15271   122656243+   7  HPFS/NTFS
/dev/sdc6           15272       30401   121531693+   7  HPFS/NTFS
igitihi@igitihi-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults                           0  0  
# /dev/sda3
UUID=138d09af-217f-45d3-9b8b-b43dd183a30c  /                 ext3         relatime,errors=remount-ro         0  1  
# /dev/sda2
UUID=0be9c550-b9af-41ad-a7c9-e73af43578e5  /boot             ext3         relatime                           0  2  
# /dev/sda4
UUID=5e8eaf6d-4716-4e6e-9a5a-3271b485540f  none              swap         sw                                 0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8              0  0  
/dev/fd0                                   /media/floppy0    auto         rw,user,noauto,exec,utf8           0  0  
/dev/sdb7                                  /media/Data2      ntfs         defaults                           0  0  
/dev/sda3                                  /media/sda3       ext3         defaults                           0  0  
/dev/sda4                                  /media/sda4       swap         defaults                           0  0  
/dev/sdb5                                  /media/Apps       ntfs         defaults                           0  0  
/dev/sdb6                                  /media/Data1      ntfs         defaults                           0  0  
/dev/sdc5                                  /media/MP31       ntfs         defaults                           0  0  
/dev/sdb4                                  /media/sdb4       swap         sw                                 0  0  
/dev/sda5                                  /media/sda5       ntfs         defaults                           0  0  
/dev/sda6                                  /media/sda6       vfat         defaults                           0  0  
/dev/sdb1                                  /media/sdb1       ntfs         defaults                           0  0  
/dev/sdb2                                  /media/sdb2       ext3         defaults                           0  0  
/dev/sdb3                                  /media/sdb3       ext3         defaults                           0  0  
/dev/sdc7                                  /media/sdc7       ntfs         defaults                           0  0  
/dev/sda1                                  /media/sda1       ntfs         nls=iso8859-1,umask=000,ro         0  0  
/dev/sda2                                  /media/sda2       ext3         defaults                           0  0  
/dev/sdd6                                  /media/External2  ntfs         nls=iso8859-1,noauto,umask=000,ro  0  0  
/dev/sdd5                                  /media/External1  ntfs         nls=iso8859-1,noauto,umask=000,ro  0  0  
/dev/sdc6                                  /media/MP32       ntfs         defaults                           0  0  
```

The drive that doesn't mount is sdc6.

Thanks for the suggestion, alienexplorers. I'll have a look.

---

### Post by iaculallad on 2008-09-05
What about using it's UUID in your fstab file:

```
gksudo gedit /etc/fstab
```

and replace:

```
/dev/sdc6                                  /media/MP32       ntfs         defaults                           0  0

```

with

```
UUID=3610B93D10B90541 /media/MP32     ntfs    defaults,umask=007,gid=46 0       1

```

Save and Close.

---

### Post by IGITIHI on 2008-09-17
Replacing the path with the UUID eventually solved the problem. Thanks a lot for your help!

---


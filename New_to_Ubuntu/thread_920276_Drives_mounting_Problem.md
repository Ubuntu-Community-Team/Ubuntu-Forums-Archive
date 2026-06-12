---
title: "Drives mounting Problem"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by tejalk on 2008-09-15
i have installed ubuntu 8.04 with Windows XP, However two partitions in the Hard disk cannot be mounted to access data. Both the partitions are in NTFS Format. Please help

---

### Post by iaculallad on 2008-09-15
> **tejalk said:**
> i have installed ubuntu 8.04 with Windows XP, However two partitions in the Hard disk cannot be mounted to access data. Both the partitions are in NTFS Format. Please help

Try auto-mounting those NTFS partition in your fstab file.

Do post your:

```
cat /etc/fstab
sudo fdisk -l
sudo blkid

```

---

### Post by tejalk on 2008-09-15
> **iaculallad said:**
> Try auto-mounting those NTFS partition in your fstab file.

Do post your:

```
cat /etc/fstab
sudo fdisk -l
sudo blkid

```
Not working , should i paste the complete code and put the code 1 by one. i am getting following message. My drives are not mounting. please help

 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e08027e9-a1d0-467c-abf1-799faabfcfef /               ext2    errors=remount-ro 0       1
# /dev/sda8
UUID=d52ce959-cb09-4284-b067-5db60a7c2650 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
tejal@tejal-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d1be5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2744    22041148+  83  Linux
/dev/sda2   *        2745        5176    19535040    7  HPFS/NTFS
/dev/sda3            5177       19456   114704100    f  W95 Ext'd (LBA)
/dev/sda5            5613       10813    41777001    7  HPFS/NTFS
/dev/sda6           10814       15351    36451453+   7  HPFS/NTFS
/dev/sda7           15352       19456    32973381    c  W95 FAT32 (LBA)
/dev/sda8            5177        5612     3502107   82  Linux swap / Solaris

Partition table entries are not in disk order
tejal@tejal-desktop:~$ sudo blkid
/dev/sda1: UUID="e08027e9-a1d0-467c-abf1-799faabfcfef" TYPE="ext2" 
/dev/sda2: TYPE="swap" UUID="d4dedb6f-8b6e-41e4-b0b3-f9499e5d0c5e" 
/dev/sda5: UUID="5122E5F64FA55E41" LABEL="MUSIC" TYPE="ntfs" 
/dev/sda6: UUID="51FF6991016ED6D0" LABEL="SOFTWARE" TYPE="ntfs" 
/dev/sda7: LABEL="DATA" UUID="46C8-4840" TYPE="vfat" 
/dev/sda8: TYPE="swap" UUID="d52ce959-cb09-4284-b067-5db60a7c2650" 
tejal@tejal-desktop:~$

---

### Post by Tatty on 2008-09-15
I assume that the two partitions you want to see are your "MUSIC" and "SOFTWARE" partitions?

If so then:

First make somewhere for them to mount to:
```
sudo mkdir /media/MUSIC
sudo mkdir /media/SOFTWARE
```

Next back up your current fstab:
```

sudo cp /etc/fstab
```

Then open your fstab for editing as superuser:

```
gksu /etc/fstab
```

Then add the following lines at the bottom of your fstab:

```
UUID="5122E5F64FA55E41" /media/MUSIC ntfs-3g defaults  0 0
UUID="51FF6991016ED6D0" /media/SOFTWARE ntfs-3g defaults 0 0
```

EDIT: Then reboot

---

### Post by drs305 on 2008-09-15
If its partitions 5 & 6 that aren't mounting, add these lines to your fstab:

```

LABEL=MUSIC /media/**mountpoint** ntfs-3g uid=1000,gid=100,umask=022 0 0
LABEL=SOFTWARE /media/**mountpoint** ntfs-3g uid=1000,gid=100,umask=022 0 0

```

Make sure the mountpoints exist, then if the partitions aren't mounted:
```
sudo mount -a
```

You can change the gid to any group you wish. The umask settings convert to 755 permissions (rwx, rx, rx).

---

### Post by acidsolution on 2008-09-15
Make sure you properly shutdown windows before starting Ubuntu 
if you have hibernated windows than ntfs partition wont mount in Ubuntu

---


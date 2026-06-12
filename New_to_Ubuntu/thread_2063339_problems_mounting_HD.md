---
title: "problems mounting HD"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by djyoung4 on 2012-09-26
I recently installed a new 12.04 install on a 40 GB HD.  I have 3 other drives in the box which are 2X1TB and 1X2TB.  The 2TB has my old 10.04 install on it but I plan on formatting the whole drive.  The other two drives are storage but I can't get them to mount.  Going through the disk utility it gives me an error saying that the daemon is inhibited.  Here is my fdisk -l
```
server@server-home:~$ sudo fdisk -l
[sudo] password for server: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b83fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1953520064   976760001    b  W95 FAT32

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdc: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00052c07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    69736447    34867200   83  Linux
/dev/sdc2        69738494    78123007     4192257    5  Extended
/dev/sdc5        69738496    78123007     4192256   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1953520064   976760001   83  Linux

```

---

### Post by Epodx64 on 2012-09-26
Whats your fstab look like

cat /etc/fstab

---

### Post by djyoung4 on 2012-09-27
```
server@server-home:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a134e42c-9aa4-41b1-9a90-7a2ea5ded5ad /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bd495572-5a90-407f-afb0-2aeabb9cd9b9 none            swap    sw              0       0

```

---

### Post by djyoung4 on 2012-09-27
So from what I can understand my other HD are not in the fstab and I need to edit it to add them to the fstab.  [This tutorial]("http://www.tuxfiles.org/linuxhelp/fstab.html") seems to explain it but I am still having problems understanding how to do that

---

### Post by djyoung4 on 2012-09-28
any ideas

---

### Post by Wim Sturkenboom on 2012-09-28
create mountpoints; as these are permanent mounts, I would create them in /mnt

```

sudo mkdir /mnt/mydisk1
sudo mkdir /mnt/mydisk2

```

determine the block IDs

```

wim@wim-desktop:~$ sudo blkid
/dev/sda1: UUID="24655031-ac78-4303-8be2-cdda59dfe86e" TYPE="ext3" 
/dev/sda2: UUID="7ea591f7-11ac-421e-b2ce-420aece15a15" TYPE="swap" 
/dev/sda5: *[COLOR="Red"]UUID="61d8e30f-6cfe-412f-8684-c7fd648cfc3d"[/COLOR]* TYPE="ext3" 
/dev/sdb1: LABEL="PENDRIVE" UUID="1517-3368" TYPE="vfat" 

```
look for UUIDs for sda1 and sdd1 (I've marked the uuid for sda5 in red italic as I will use that below)

modify /etc/fstab (example for one disk shown in italic red); you need root permissions so use sudo / gksudo
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a134e42c-9aa4-41b1-9a90-7a2ea5ded5ad /               ext4    errors=remount-ro 0       1

[I][COLOR="Red"]UUID=61d8e30f-6cfe-412f-8684-c7fd648cfc3d /mnt/mydisk1    ext3    defaults        0       2
[/COLOR][/I]

# swap was on /dev/sda5 during installation
UUID=bd495572-5a90-407f-afb0-2aeabb9cd9b9 none            swap    sw    

```
Make sure that the type matches the type as found by blkid (in this case ext3)

Manually mount (or reboot)
```

sudo mount /mnt/mydisk1

```

Adjust to your needs!

---

### Post by djyoung4 on 2012-09-29
thanks so much.  that worked perfectly

---

### Post by Wim Sturkenboom on 2012-09-29
> **djyoung4 said:**
> thanks so much.  that worked perfectlyGreat; please mark your thread as solved using the thread tools just above the first post on the page.

---


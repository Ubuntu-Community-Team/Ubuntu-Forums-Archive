---
title: "USB hard drive not mounting"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by sauravbhaumik on 2013-12-12
Hello

I have two old USB hard drives, which mount easily on my Ubuntu 11.04.

Yesterday I bought a Seagate Backup Plus 1TB USB hard disk; it did not mount.

I have Windows XP installed in my computer as a dual boot. The Backup Plus mounts easily on the Windows XP. 

I reformatted the Backup Plus using ntfs in XP and tried to mount it on Ubuntu again, but it didn't mount.

I have a Ubuntu 13.10 USB stick. I booted using the stick, and the Backup Plus mounted. Here is a snapshot from the live usb.

[ATTACH=CONFIG]248558[/ATTACH]

In order to compare, I attach a screenshot of disk utility from my Ubuntu 11.04

[ATTACH=CONFIG]248559[/ATTACH]

I created a folder called "Backup Plus" in my home. Now if I want to mount /dev/sdb on that folder, it says

```
saurav@reflexion:~$ sudo mount /dev/sdb ~/Backup\ Plus/
mount: /dev/sdb is not a valid block device
```

Here is the output of fdisk -l, and you can see the two partitions (/dev/sdj1 and /dev/sdj2) of my old 500GB USB hard drive, but no sign of the Backup Plus.

```
saurav@reflexion:~$ sudo fdisk -l
[sudo] password for saurav: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3952    31744408+   c  W95 FAT32 (LBA)
/dev/sda2            3953        7680    29945160   83  Linux
/dev/sda3            7681        7810     1044152   82  Linux swap / Solaris
/dev/sda4            7811       38914   249837399    f  W95 Ext'd (LBA)
/dev/sda5           11690       23606    95723271    7  HPFS/NTFS
/dev/sda6           23607       38914   122951680    7  HPFS/NTFS
/dev/sda7            7811       11689    31158004+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdj: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057efe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1       30401   244196001    7  HPFS/NTFS
/dev/sdj2           30402       60801   244188000    7  HPFS/NTFS
saurav@reflexion:~$ 

```

At present it is difficult for me to upgrade to a later version of Ubuntu. Could you kindly tell me a possible way to mount the Backup Plus hard drive on my Ubuntu 11.04?

Thanks in advance.

Saurav Bhaumik

---

### Post by asus-user on 2013-12-13
> **sauravbhaumik said:**
> Hello

I have two old USB hard drives, which mount easily on my Ubuntu 11.04.

Yesterday I bought a Seagate Backup Plus 1TB USB hard disk; it did not mount.

I have Windows XP installed in my computer as a dual boot. The Backup Plus mounts easily on the Windows XP. 

I reformatted the Backup Plus using ntfs in XP and tried to mount it on Ubuntu again, but it didn't mount.

I have a Ubuntu 13.10 USB stick. I booted using the stick, and the Backup Plus mounted. Here is a snapshot from the live usb.

[ATTACH=CONFIG]248558[/ATTACH]

In order to compare, I attach a screenshot of disk utility from my Ubuntu 11.04

[ATTACH=CONFIG]248559[/ATTACH]

I created a folder called "Backup Plus" in my home. Now if I want to mount /dev/sdb on that folder, it says

```
saurav@reflexion:~$ sudo mount /dev/sdb ~/Backup\ Plus/
mount: /dev/sdb is not a valid block device
```

Here is the output of fdisk -l, and you can see the two partitions (/dev/sdj1 and /dev/sdj2) of my old 500GB USB hard drive, but no sign of the Backup Plus.

```
saurav@reflexion:~$ sudo fdisk -l
[sudo] password for saurav: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3952    31744408+   c  W95 FAT32 (LBA)
/dev/sda2            3953        7680    29945160   83  Linux
/dev/sda3            7681        7810     1044152   82  Linux swap / Solaris
/dev/sda4            7811       38914   249837399    f  W95 Ext'd (LBA)
/dev/sda5           11690       23606    95723271    7  HPFS/NTFS
/dev/sda6           23607       38914   122951680    7  HPFS/NTFS
/dev/sda7            7811       11689    31158004+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdj: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057efe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1       30401   244196001    7  HPFS/NTFS
/dev/sdj2           30402       60801   244188000    7  HPFS/NTFS
saurav@reflexion:~$ 

```

At present it is difficult for me to upgrade to a later version of Ubuntu. Could you kindly tell me a possible way to mount the Backup Plus hard drive on my Ubuntu 11.04?

Thanks in advance.

Saurav Bhaumik

To mount a ntfs drive sdb1, type in Terminal this command (replace <path> with the directory path where you want to mount the drive into):

```
sudo mount -t ntfs-3g /dev/sdb1 <path>
```

Refer to: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) for some details and explanations.

---

### Post by sauravbhaumik on 2013-12-13
Thanks. But it does not work.
```
saurav@reflexion:~$ sudo mount -t ntfs-3g /dev/sdb1 ~/seaget
[sudo] password for saurav: 
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
```

---

### Post by sauravbhaumik on 2013-12-13
Hello
The following seems to work
```
sudo modprobe -r uas
```

---

### Post by asus-user on 2013-12-13
good to know :)

---

### Post by squakie on 2013-12-13
Keep this in mind, as this could be part of your problem:

USB device designations change - what is /deb/sdb1 one day could be /dev/sxx the next.  Run the following in terminal while the USB drive is plugged in:

sudo blkid

This will show the drives and their UUID's.  The UUID is unique to a volume and is what you should be using to mount you USB drive(s):

sudo mount UUID="xxxxxxxxxxxxxx" -t ntfs  <your mount point path> 

I'm not sure you actually need to specify ntfs-3g - I don't and it at least seems to work.  Someone else may comment about that if it is needed.

You can also add this to the fstab so it will do it automatically.  If the drive isn't connected at boot you will get a message and need to acknowledge it before the boot will continue.  There is a parameter to bypass that, but the user I heard about it from recommended it in one thread, then changed course in another and said not to use it.  So for now, bet the mount working manually, then you can create a simple script to execute to mount it, and/or you can add it fstab.

---


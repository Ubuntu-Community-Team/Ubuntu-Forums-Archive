---
title: "[SOLVED] Screwed NTFS partition mount"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Zero7 on 2008-11-03
I clicked on the mounted NTFS partition (sda1)in desktop and in properties added mount location (yesterday).  After the reboot I am not able to access the partition. Error is shown in attachment.
I know I screwed it myself, but need help now:) Thanks in advance.
___________________________________________________
sudo fdisk -l

[sudo] password for home: 



Disk /dev/sda: 30.0 GB, 30005821440 bytes

255 heads, 63 sectors/track, 3648 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xf545f545



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        2295    18434556    7  HPFS/NTFS

/dev/sda2            2296        2805     4096575   83  Linux

/dev/sda3            3584        3648      522112+  82  Linux swap / Solaris

/dev/sda4            2806        3583     6249285   83  Linux



Partition table entries are not in disk order

________________________________________________________________________
# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda2

UUID=1cbb4636-fbe5-49e9-a9cf-2a20b931b70d /               ext2    relatime,errors=remount-ro 0       1

# /dev/sda4

UUID=160a611e-0f90-46c6-9e5f-2af3031043ec /home           ext3    relatime        0       2

# /dev/sda3

UUID=d9a2aeeb-0d29-4083-baac-c8cb95a67c74 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
___________________________________________________________________

dev/sda2 / ext2 rw,relatime,errors=remount-ro 0 0

tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0

/proc /proc proc rw,noexec,nosuid,nodev 0 0

sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0

varrun /var/run tmpfs rw,nosuid,mode=0755 0 0

varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0

udev /dev tmpfs rw,mode=0755 0 0

tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0

devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0

fusectl /sys/fs/fuse/connections fusectl rw 0 0

lrm /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=755 0 0

/dev/sda4 /home ext3 rw,relatime 0 0

securityfs /sys/kernel/security securityfs rw 0 0

binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

gvfs-fuse-daemon /home/home/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=home 0 0

---

### Post by drs305 on 2008-11-03
I'm not sure exactly what you have done to change the mountpoint but since it is not currently listed in fstab perhaps the easiest thing to do would be to install 'ntfs-config'. After installing, it will ask for a mountpoint and create an fstab entry which will mount the partition during boot. 'ntfsprogs' is a good utility to have (for labeling ntfs partitions and allowing older versions of gparted to work with them), so I've included it in the install line. You may disregard it if you wish.

To install, via synaptic or:
```

sudo apt-get install ntfs-config ntfsprogs

```

To run:
System Tools, NTFS Configuration Tool
Select Internal Drive
Enter the *mountpoint* when asked, it will be located at /media/*mountpoint*

---

### Post by kk0sse54 on 2008-11-03
It's looks as though you've screwed up the mount point for that partition. Create a mount point in /media and then in the terminal try ```
mount /dev/sda1 /media/<folder_name>
``` see if that works, you could then add the partition to your fstab so that you make sure it mounts to a valid folder.

---

### Post by Zero7 on 2008-11-04
> **C!oud said:**
> It's looks as though you've screwed up the mount point for that partition. Create a mount point in /media and then in the terminal try ```
mount /dev/sda1 /media/<folder_name>
``` see if that works, you could then add the partition to your fstab so that you make sure it mounts to a valid folder.
Thanks! This worked. To show you what I had done, here is the screenshot of the screwup.

---

### Post by kk0sse54 on 2008-11-05
> **Zero7 said:**
> Thanks! This worked. To show you what I had done, here is the screenshot.

Glad you got it working :)

---


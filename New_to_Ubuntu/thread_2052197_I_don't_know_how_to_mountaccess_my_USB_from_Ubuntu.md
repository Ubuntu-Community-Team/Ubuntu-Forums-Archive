---
title: "I don't know how to mount/access my USB from Ubuntu Server"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by Zukaro on 2012-09-02
I can't figure out how to access my USB from Ubuntu Server (I've tried mounting /dev/sdb1 but it tells me it's not there; I've also looked in /media and all I find is cdrom (which is present even when the USB isn't connected)).

I'm not sure what to do.

---

### Post by Hadaka on 2012-09-02
Hi, here are a few ways to verify the os sees it.
and by the way..what version of ubuntu are you using...12.04?

enter this in terminal   ctrl/alt/t

```
lsusb
```

you should also see it in the left launch panel

you can click HOME FOLDER, you should see it listed in the far left side
under DEVICES

you can also click the DASH icon..type in DISK, then click Disk Utility...it should also
be listed there.

if you cant see it in any of these places...its not working.

---

### Post by Zukaro on 2012-09-02
I'm using Ubuntu Server 12.04.1

There's no GUI so I need to do it through the terminal (I have a bit of experience with the terminal but I've never mounted anything, so I'm completely new when it comes to that :P).


lsusb shows the USB (thanks).  Not sure how to mount it though.  Do I take the ID and mount to that?

---

### Post by steeldriver on 2012-09-02
If it's already mounted (you just don't know where) then 

```
df
```or
```
mount
```(with no arguments) should tell you. OTOH if it's unmounted then

```
sudo fdisk -l
```should list all the available devices/partitions, you should be able to figure out which is the USB device based on size / label / fs type

---

### Post by Zukaro on 2012-09-02
This is what df says:

Filesystem                   1K-blocks    Used Available Use% Mounted on
/dev/mapper/Server-root  79048348 2421848  72667512   4% /
udev                            467904       4    467900   1% /dev
tmpfs                           190796     304    190492   1% /run
none                              5120       0      5120   0% /run/lock
none                            476980       0    476980   0% /run/shm
/dev/sda1                       233191   24988    195762  12% /boot



This is what mount says:

/dev/mapper/Server-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /boot type ext2 (rw)



This is what lsusb says:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 001 Device 005: ID 03f0:3d07 Hewlett-Packard




I'm not sure which one of those is my USB in mount and df (I know my USB is the bottom one in lsusb).

---

### Post by steeldriver on 2012-09-02
it doesn't appear to be mounted - so run the 'sudo fdisk -l' command please

---

### Post by Zukaro on 2012-09-02
This is what it says when I run it:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8019

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   160835583    80166913    5  Extended
/dev/sda5          501760   160835583    80166912   8e  Linux LVM

Disk /dev/mapper/Server-root: 81.1 GB, 81080090624 bytes
255 heads, 63 sectors/track, 9857 cylinders, total 158359552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/Server-root doesn't contain a valid partition table

Disk /dev/mapper/Server-swap_1: 1006 MB, 1006632960 bytes
255 heads, 63 sectors/track, 122 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/Server-swap_1 doesn't contain a valid partition table

Disk /dev/sdb: 16.2 GB, 16170164224 bytes
64 heads, 32 sectors/track, 15421 cylinders, total 31582352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?   778135908  1919645538   570754815+  72  Unknown
/dev/sdb2   ?   168689522  2104717761   968014120   65  Novell Netware 386
/dev/sdb3   ?  1869881465  3805909656   968014096   79  Unknown
/dev/sdb4   ?  2885681152  2885736650       27749+   d  Unknown

Partition table entries are not in disk order

---

### Post by steeldriver on 2012-09-02
so what kind of USB device are we looking for here exactly? sdb is a 16GB device - but it's partitioned somewhat interestingly - is that what you expect?

---

### Post by Zukaro on 2012-09-02
My USB is 16GB, but when I try to mount /dev/sdb it tells me it's not in the fstab or something like that and doesn't mount.

---

### Post by steeldriver on 2012-09-02
Well it doesn't understand the partition types on the device - even if you try to manually mount them you'd need an fstype to give to the mount command (via the -t option)

Do you have data on there you're trying to save? if not I would consider reformating it

Otherwise I think you will need to find out what fs is on the partition(s) you want to save, and add the appropriate fs support for them - if that's even available

---

### Post by daageep on 2012-09-02
Hi,

This link will be useful to you: [Fstab]("https://help.ubuntu.com/community/Fstab")

Basically you need to add a link in fstab for your usb drive. Lets assume that it is formatted as NTFS and you want to mount it via its UUID (instead of /dev/sdX), then issue the command 

sudo blkid 

and copy down the UUID associated with your drive. Then go to /media/ and create a directory (whatever you want to call it). lets say you want the name to be FLASH then type 

sudo mkdir FLASH 

Finally, edit the fstab file (e.g. sudo nano /etc/fstab) and add a line like 

UUID_you_obtained_earlier /media/FLASH ntfs-3g auto defaults,locale=en_US.utf8 0 0

To mount the drive, type "sudo mount /media/FLASH". You should be all ready to go! Of course, adapt these instructions with the link I provided earlier for your situation. Good luck

---

### Post by Zukaro on 2012-09-02
> **steeldriver said:**
> Well it doesn't understand the partition  types on the device - even if you try to manually mount them you'd need  an fstype to give to the mount command (via the -t option)

Do you have data on there you're trying to save? if not I would consider reformating it

Otherwise I think you will need to find out what fs is on the  partition(s) you want to save, and add the appropriate fs support for  them - if that's even available



I'll try reformatting it then mounting it.

---

### Post by Zukaro on 2012-09-03
Re-formatting it didn't work, but daageep's suggestion worked (adding it to the fstab).  It's working now; thanks.

---


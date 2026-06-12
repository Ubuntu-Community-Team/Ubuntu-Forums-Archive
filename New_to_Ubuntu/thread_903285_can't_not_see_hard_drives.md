---
title: "can't not see hard drives"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by konos on 2008-08-28
i use a trust 7 port hub.
All the devices (hard disks) which are connected on the hubs are not present.
what should i do?? is it a matter of mounting the devices..?
thenx

---

### Post by kpkeerthi on 2008-08-28
Can you post the output of ```
sudo fdisk -l
``` with all the HDDs connected and turned on?

---

### Post by konos on 2008-08-28
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1934    15534823+   7  HPFS/NTFS
/dev/sda2            1935        4726    22426740    f  W95 Ext'd (LBA)
/dev/sda5            2667        4726    16546918+   7  HPFS/NTFS
/dev/sda6            1935        2627     5566459+  83  Linux
/dev/sda7            2628        2666      313236   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6323eba9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS

---

### Post by kpkeerthi on 2008-08-28
OK... it lists one 250 GB, NTFS formatted drive (/dev/sdb). Is that all you have? Or more? Do you want to mount this?

Can you also post the output of **mount** command?

---

### Post by konos on 2008-08-28
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/konos/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=konos)

i have a 500GB EXTERNAL and a 40G external

---

### Post by ByteJuggler on 2008-08-28
Please post the output of:

```
sudo lsusb
```

---

### Post by kpkeerthi on 2008-08-28
> **konos said:**
> 
i have a 500GB EXTERNAL and a 40G external

I'm sorry but ubuntu did not detect these as you can see from the fdisk output. 

Can you try connecting one of these, for now, directly to the USB port of your computer and post the output of **sudo fdisk -l** as before? 

You may have to wait for a few seconds after connecting the device and then run the fdisk command.

---

### Post by kpkeerthi on 2008-08-28
Please include command outputs between [code] tags so they are easy to read.

---

### Post by konos on 2008-08-28
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1934    15534823+   7  HPFS/NTFS
/dev/sda2            1935        4726    22426740    f  W95 Ext'd (LBA)
/dev/sda5            2667        4726    16546918+   7  HPFS/NTFS
/dev/sda6            1935        2627     5566459+  83  Linux
/dev/sda7            2628        2666      313236   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6323eba9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x454c68b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9729    78148161    b  W95 FAT32

---

### Post by kpkeerthi on 2008-08-28
To mount the NTFS drive, see [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

I hope the other FAT32 formatted drivers were automounted.

What is the output of **mount** command?

---

### Post by konos on 2008-08-28
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/konos/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=konos)
/dev/sdc1 on /media/WD 500GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdd1 on /media/LaCie type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by konos on 2008-08-28
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/konos/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=konos)
/dev/sdc1 on /media/WD 500GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by konos on 2008-08-28
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/konos/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=konos)
/dev/sdc1 on /media/WD 500GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by egalvan on 2008-08-28
Is this a powered hub? That is,k does it have it's own, separate power supply?

If not, it is probably over-loaded, and the drives may not be initializing right.

---

### Post by konos on 2008-08-28
yes it has power supply...

---

### Post by egalvan on 2008-08-28
> **konos said:**
> yes it has power supply...

What is the capacity of the power supply?

What devices do you have connected to the hub?

And, have you tried this same setup under WinXP?

ErnestG

:popcorn:

---

### Post by konos on 2008-08-28
it used to work until yesterday..
i don'n know the capacity..
connected divices a printer, a card reader and a hard disk
the usb hub is not recogizized by WinXp...

---

### Post by egalvan on 2008-08-28
> **konos said:**
> i don't know the capacity..
Watts/voltage/amps should be stamped/printed on the power adapter


> i have a 500GB EXTERNAL and a 40G external
> connected divices a printer, a card reader and a hard disk
Is it one or two drives?


> the usb hub is not recogizized by WinXp...

> **konos said:**
> it used to work until yesterday..
Was it ever recongnized by XP?
Was it ever recognized by Ubuntu?

Try this; connect just the hub to XP.

If XP complains, then you have a defective hub (or power supply).
If XP doesn't see the hub at all, then you either have a totally dead hub (or power supply) or a dead cable.

If it works, then connect the printer ( I assume it worked before under XP)
If that works, then add each item one by one, until all are added, or XP has a problem.

Yeah, I know, this sounds like a lot of work,
 but attacking the problem systematically will give a better chance of finding the problem.


ErnestG

:popcorn:

---


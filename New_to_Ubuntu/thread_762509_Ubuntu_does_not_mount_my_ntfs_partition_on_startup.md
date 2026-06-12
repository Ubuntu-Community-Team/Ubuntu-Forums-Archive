---
title: "Ubuntu does not mount my ntfs partition on startup, but it was ok before."
date: 2008-04-22
forum: New to Ubuntu
---

### Post by legolas_w on 2008-04-22
I have problem with using NTFS partitions
Problem is that I think linux faced a problem and does not detect my NTFS drives which previously I was using.
I have many short cut to my NTFS partition files and now All of them has no ICON and there is lock on each short cut.
I should say that I restart the linux un-normally by using hard restart bottom.

Can some one please let me know how I can fix it?

thanks.

---

### Post by hums07 on 2008-04-22
Can you post the output of these instructions?
```
sudo fdisk -l
cat /etc/fstab
mount
```

or you may need to fsck

---

### Post by bazzawill on 2008-04-22
This happens to me when windows does not shut down properly or other reasons and I have to manually mount the drives in a terminal use
```
ls /dev/[hs]da*
``` 
this will give you a list of your drives fyi hdX (X is a representation of any letter starting with a)is pata drives sdX is sata drives
you should get something like hda and hda1 etc hda on it's own is the drive any number after that is the partitions on that drive
 if you can determine which drive you want or just try them all
```
 cd /media
ls 
```
make sure the mount point for the device you are mounting (hda1, sda1, etc)
to mount the drive use this as an example for hda1
```

sudo mount -t ntfs-3g -o force /dev/hda1 /media/hda1

```
I hope this makes some sense

---

### Post by legolas_w on 2008-04-22
Hi, Thank you. here is the outputs:

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c212

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2           12749       19122    51199155    7  HPFS/NTFS
/dev/sda3           19123       38487   155549362+   f  W95 Ext'd (LBA)
/dev/sda4            6375       12748    51199155   83  Linux
/dev/sda5           19123       38244   153597433+   7  HPFS/NTFS
/dev/sda6           38245       38487     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08e408e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       15298    61440592+   f  W95 Ext'd (LBA)
/dev/sdb3           15299       24321    72477247+   7  HPFS/NTFS
/dev/sdb5            7650       15043    59392273+   7  HPFS/NTFS


```

second command:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=df9e01b9-f029-43a1-92a7-e0dde840c15b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=03D3CDD776EC418C /media/sda1     ntfs    defaults,umask=007,gid=46, 0       1
# /dev/sda2
UUID=624802FD2492A01A /media/sda2     ntfs    defaults,umask=007,gid=46, 0     1
# /dev/sda5
UUID=24D82AA04F794E57 /media/sda5     ntfs    defaults,umask=007,gid=46, 0       1
# /dev/sdb1
UUID=7EA48CF3A48CAF69 /media/sdb1     ntfs    defaults,umask=007,gid=46, 0     1
# /dev/sdb5
UUID=8AE49887E4987764 /media/sdb5     ntfs    defaults,umask=007,gid=46, 0       1
# /dev/sda6
UUID=161a9a0f-e3d3-41a2-9a74-cb54a36e9f42 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


```

and the last command:

```

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)


```

Thank you for the help.

---

### Post by russo.mic on 2008-04-22
> **bazzawill said:**
> This happens to me when windows does not shut down properly or other reasons and I have to manually mount the drives in a terminal use
```
ls /dev/[hs]da*
``` 
this will give you a list of your drives fyi hdX (X is a representation of any letter starting with a)is pata drives sdX is sata drives
you should get something like hda and hda1 etc hda on it's own is the drive any number after that is the partitions on that drive
 if you can determine which drive you want or just try them all
```
 cd /media
ls 
```
make sure the mount point for the device you are mounting (hda1, sda1, etc)
to mount the drive use this as an example for hda1
```

sudo mount -t ntfs-3g -o force /dev/hda1 /media/hda1

```
I hope this makes some sense

OR....you could just start Windows, then shut it down normally.  The above command should only be used if you CAN'T start the NTFS partition.  the force command does just what it says.  You could do some damage to the ntfs filesystem.

Russo

---

### Post by PmDematagoda on 2008-04-22
You can also run ntfsfix on it so that a force mount would not be needed.

---

### Post by hums07 on 2008-04-22
You've got plenty NTFS partitions.
I would agree with PmDematagoda because you did hard reboot in Ubuntu. After that, try to mount them manually. There will be a message if it doesnot work.

---

### Post by dark_harmonics on 2008-04-22
Yes the only time i have an issue with mounting my NTFS drives is if I did an "unclean" disconnect (i use NTFS on my usb stick to fix windows machines). If i just pull the drive instead of disconnecting properly in windows, then it needs forced. They are not kidding that this can crash your partition as it happened to me once on the usb stick. Luckily i dont keep any sensitive information on there (just tools n stuff).

so basically i am +1 for booting into windows normally and then shutting down properly.

---

### Post by legolas_w on 2008-04-22
Thank you, It get fixed by restarting the computer, letting windows start and then shutting it down properly.

Thanks.

---

### Post by Joeb454 on 2008-04-22
This is usually the case...it is a pain, especially if your Windows boot time is 2-3 minutes ;) Think of what I could've done in that time.

Glad you got it fixed though

---


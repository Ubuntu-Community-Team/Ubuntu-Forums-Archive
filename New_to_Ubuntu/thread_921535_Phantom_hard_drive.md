---
title: "Phantom hard drive"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Tom G Marseille on 2008-09-16
After a couple of worrying hours where I was sure I'd completely screwed up, I am relieved to write about what is merely annoying...

When I boot up, I get a message saying there is no superblock on hdb1 or it is not ext2...  After ctrl-D the machine boots up correctly.

There was an hdb1, which somehow (that's where I screwed up) became \home.  I have now physically removed the drive, but the system keeps looking for it :-(

I'm running Hardy Heron 8.04
Kernel Linux 2.6.24-19-generic
GNOME 2.22.3

AMD Athlon 64 3500+
500 MB RAM

1 hd 5 partitions 
hda1 ext3 /
hda2 extended
hda3 linux-swap
hda4 ext3 /home
hda5 ntfs /media/hda5

Hope you can help!

Tom

---

### Post by mcduck on 2008-09-16
Could you post here the outputs of following commands:
```

sudo fdisk -l
cat /etc/fstab
```

Most likely your problem is that the /etc/fstab file still has an entry for the second hard drive, and because of that Ubuntu tries to mount it during boot (which obviously fails..).

---

### Post by Tom G Marseille on 2008-09-17
sudo fdisk -l gives

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0f4a0f4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            6375       24320   144151245    f  W95 Ext'd (LBA)
/dev/hda3            1217        1459     1951897+  82  Linux swap / Solaris
/dev/hda4            1460        6374    39479737+  83  Linux
/dev/hda5            6375       24320   144151213+   7  HPFS/NTFS

Partition table entries are not in disk order
--------------------------------------------------------------------------
cat /etc/fstab gives

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=7406e2ae-7fb6-4d3d-8a64-c10aa973a658 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=4a876160-2134-4b02-b0e9-f1d2b7044c5c /home           ext3    defaults        0       2
# /dev/hda5
UUID=C46C24166C2405B0 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=65f9eb04-f0a0-45e5-9698-32fd04c8a4f0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1	/media/hdb1     ext3    defaults        0       2
-------------------------------------------------------------------------

So I can now see where the problem comes from, I think!  But how can I edit fstab?

---

### Post by mcduck on 2008-09-17
Just press Alt-F2 and run "gksudo gedit /etc/fstab" (if you want to d it in Gnome) or alternatively run "sudo nano /etc/fstab" (to edit from command line).

Remove the last line, save, and the problem is gone. :)

---

### Post by Tom G Marseille on 2008-09-17
Brilliant, thankyou :)

Tom

---


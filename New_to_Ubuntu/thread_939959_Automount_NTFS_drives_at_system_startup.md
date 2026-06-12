---
title: "Automount NTFS drives at system startup"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by anksrivastava on 2008-10-06
I wish to auto mount NTFS drives at system startup. I have tried ntfs-conf. It does not do it. Can anyone tell me how to do it.

Details of my fstab are:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a0187b4e-440f-4d41-9629-beaaeade728e /               ext3    relatime,errors=remount-ro 0       0
# /dev/sdb2
UUID=f65ae240-ae76-4e9e-9b7e-689740381c7e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Titan8990 on 2008-10-06
Post the output of the following


sudo blkid


sudo fdisk -l


Is this drive internal or USB?

---

### Post by anksrivastava on 2008-10-06
The drive is internal. I have two HDD.

O/P of sudo bilkid:

/dev/sda2: UUID="5AC0014FC0013335" LABEL="WinXP" TYPE="ntfs" 
/dev/sda3: UUID="A488326D88323E5C" LABEL="Junk" TYPE="ntfs" 
/dev/sda5: UUID="6630B46830B440BB" LABEL="Documents" TYPE="ntfs" 
/dev/sdb1: UUID="a0187b4e-440f-4d41-9629-beaaeade728e" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="f65ae240-ae76-4e9e-9b7e-689740381c7e" 
/dev/sdb3: UUID="429811CB9811BDFB" LABEL="Chotu" TYPE="ntfs" 

O/P of sudo fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26ed26ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        3916    31447237+   f  W95 Ext'd (LBA)
/dev/sda2   *        3917        7832    31455270    7  HPFS/NTFS
/dev/sda3            7833       30401   181285492+   7  HPFS/NTFS
/dev/sda5               2        3916    31447206    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f670f66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2490    20000893+  83  Linux
/dev/sdb2            2491        2561      570307+  82  Linux swap / Solaris
/dev/sdb3            2562        4865    18506880    7  HPFS/NTFS

---

### Post by mihaiv on 2008-10-06
Add to fstab something like this:
/dev/sda1 /media/sda1     ntfs-3g    defaults 0 0

Replace sda1 in the example with your actual ntfs drive. You need to create the /media/your_drive folder. To find out what ntfs drives you have available run:
sudo fdisk -l

---

### Post by Titan8990 on 2008-10-06
Alright, lets take /dev/sda2 as an example.

First we need to create a directory that we would like sda2 to automount to:


sudo mkdir /media/sda2


Then we take the UUID that was found from blkid: UUID=5AC0014FC0013335

We can now combine these things in to a line in /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=a0187b4e-440f-4d41-9629-beaaeade728e / ext3 relatime,errors=remount-ro 0 0
# /dev/sdb2
UUID=f65ae240-ae76-4e9e-9b7e-689740381c7e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
# /dev/sda1
UUID=5AC0014FC0013335 /media/sda2 ntfs defaults 0 0
```


The last line will cause /dev/sda2 to automount to /media/sda2

---

### Post by anksrivastava on 2008-10-06
Thanks!!
Going to try this change.

---

### Post by wvpv on 2008-11-01
I was able to use the pysdm application to mount my hard drive very easily, it's available in Add/Remove Applications. Hope this helps

---

### Post by kjaggu on 2008-11-10
> **wvpv said:**
> I was able to use the pysdm application to mount my hard drive very easily, it's available in Add/Remove Applications. Hope this helps
Thanks a lot for the help 'wvpv'.

Regards,
Jagadeesh

---


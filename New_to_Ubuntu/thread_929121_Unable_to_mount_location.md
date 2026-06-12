---
title: "Unable to mount location"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by kuproverto on 2008-09-24
I installed a second internal HD. It appeared as SCSI Drive in Places | Computer but I can't access the drive. The error message is:

===
Unable to mount location
Can't mount file
===

How do I access this drive? Should it be formatted in some way?

---

### Post by perlluver on 2008-09-24
> **kuproverto said:**
> I installed a second internal HD. It appeared as SCSI Drive in Places | Computer but I can't access the drive. The error message is:

===
Unable to mount location
Can't mount file
===

How do I access this drive? Should it be formatted in some way?

If the disk is brand new, than yes it has to be formatted, if it will be for Linux only, I would recommend Ext-3 or one of the Linux file systems, if it will be used with windows too, then ntfs, would be good for that.

---

### Post by kuproverto on 2008-09-24
It is for Linux only. Would you let me know how to format it please?

---

### Post by lwvmobile on 2008-09-24
Please Post the output of 

```
sudo fdisk -l
```

Most modern disk controllers, especially in ubuntu, show up as SCSI, or rather as sba sdb etc.

---

### Post by perlluver on 2008-09-24
Do what lwvmovile said, then if it needs formatting, open up System>Administration>Synaptic, and install gparted.  That will allow you to format it, but be careful with this software.

---

### Post by bodhi.zazen on 2008-09-24
If it is a brand new disk you will need to write a partition table to it. You can use either a GUI tool :

see : [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)


Or the command line:

fdisk : [http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

mkfs.ext3 : [http://linux.die.net/man/8/mkfs](http://linux.die.net/man/8/mkfs)

[http://linux.die.net/man/8/mkfs.ext3](http://linux.die.net/man/8/mkfs.ext3)

---

### Post by kuproverto on 2008-09-25
Here's the output of sudo fdisk -l


```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006e78c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29268   235095178+  83  Linux
/dev/sda2           29269       30401     9100822+   5  Extended
/dev/sda5           29269       30401     9100791   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

---

### Post by kuproverto on 2008-09-25
I followed the instructions [here]("http://www.noourl.com/r8E") and all is well except for the last part, ...an entry needs to be added to the /etc/fstab file.

I added the drive details to the fstab file but it won't save due to me not having the necessary permissions.

Also, I can't copy files to the new drive due to a permission denied error and I can't create files or folders due to these options being grayed out.

---


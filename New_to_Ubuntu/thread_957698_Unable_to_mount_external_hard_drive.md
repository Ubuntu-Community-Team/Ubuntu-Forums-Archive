---
title: "Unable to mount external hard drive"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by WizardMagus on 2008-10-24
I am currently running Hardy on an HP Pavilion dv6000, and I bought a Buffalo 500 GB DriveStation Turbo external hard drive.  

I plugged it into the USB drive, and my computer seems to recognize something is plugged in.  However, when I open the Computer file, and click on "USB Drive" it says "Unable to mount location" and below that "Can't mount file."

This is the content of my fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b8b65fb-d636-4103-b34a-7cb3452a4aeb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8a5f2323-2be8-44f4-b0a6-723777eb1de8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I've seen various threads, but their fstab file seems to look a bit different, so I figured I would rather be safe than sorry.

One last piece: I read online that the drive comes formatted FAT32, but can be reformatted to NTFS if so desired.  Could that be a problem?  And if so, how do I reformat it?

Any ideas?  Do I need to provide any more information?  Thanks.

---

### Post by Crandom on 2008-10-24
Reformatting to ntfs is no problem, not that ubuntu has the ntfs-3g project installed. To format to ntfs, type this command:
```
sudo apt-get install gparted
```
then go to System > Administration > Partition Editor. Select the external hdd on the drop down menu on the right, then right click on the FAT32 partition and delete it. Then right click in the empty space and create a new ntfs partition. Apply. All files on the drive will be lost.

I have no idea about your mounting problems. Mabye a reformat will solve that.

---

### Post by MusicMastaMike on 2008-10-24
Can you plug the drive in and in a terminal, type ```
sudo fdisk -l
``` and post the output?

---

### Post by drs305 on 2008-10-24
I think Crandom meant:
```
Reformatting to ntfs is no problem, ***now*** that ubuntu has the ntfs-3g project installed.
```

Depending on the version of gparted you have, you may have to install **ntfsprogs** to format a partition to NTFS. The livecd version of gparted will do it by default, as will versions 3.8 and later (I know 3.5 won't by default). 

You can check your version's capabilities by opening gparted and then clicking on Gparted, Show Features. If the NTFS 'Create' column is checked, you are good to go. If it isn't, then install ntfsprogs and restart gparted:
```
sudo apt-get install ntfsprogs
```

---

### Post by WizardMagus on 2008-10-24
> **MusicMastaMike said:**
> Can you plug the drive in and in a terminal, type ```
sudo fdisk -l
``` and post the output?

Here is the output:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

That last bit seems interesting...

---

### Post by MusicMastaMike on 2008-10-24
This could either mean that the partitions are indeed messed up (in which case you just need to reformat it) or there's some other problem.  For instance, one of my external drives has a bad power supply, and if it's not connected just right, it will say that.

---

### Post by WizardMagus on 2008-10-24
> **Crandom said:**
> Reformatting to ntfs is no problem, not that ubuntu has the ntfs-3g project installed. To format to ntfs, type this command:
```
sudo apt-get install gparted
```
then go to System > Administration > Partition Editor. Select the external hdd on the drop down menu on the right, then right click on the FAT32 partition and delete it. Then right click in the empty space and create a new ntfs partition. Apply. All files on the drive will be lost.

I have no idea about your mounting problems. Mabye a reformat will solve that.

Gparted said that the external hard drive was completely unformatted.  It wasn't even in FAT32, which it allegedly shipped with.  Now that I formatted the hard drive, it works perfectly.

Thanks everyone for your help!

---

### Post by Hoora on 2008-12-04
WizardMagus: Did you reformat it to NTFS? Is it working well? 

I bought recently a Buffalo Drivestation Eco 1TB and I'm thinking of formatting it to NTFS or ext3, any ideas which would be better in the case of performance? I am dual booting with Ubuntu 8.10 and XP, and I can use all the partitions on the internal harddisks (ext3, NTFS) from both OS's so hopefully a non-native filesystem won't be a problem on an external drive. *knocking the wood*

---


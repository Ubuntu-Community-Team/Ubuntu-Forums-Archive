---
title: "Boot Loader Error"
date: 2014-08-18
forum: New to Ubuntu
---

### Post by anthony39 on 2014-08-18
Hello :)

My name is Anthony and I've busted my partitions. Here is a handy URL with all the data: [http://paste.ubuntu.com/8078147](http://paste.ubuntu.com/8078147)

Regarding the following, Iceland is the Windows 7 install I can't boot into, Antarctic is where I wanted to place Linux and Greenland is my data partition.

/dev/sda2        78A4C77BA4C73B00                       ntfs       Iceland
/dev/sda3        B86256CB62568E4E                       ntfs       Antarctic
/dev/sda4        A294CCF594CCCCCB                       ntfs       Greenland
Thank you very very much for any help you might be able to offer :)

Many many thanks from Anthony

---

### Post by ajgreeny on 2014-08-18
I presume you are aware that this is a Ubuntu forum, not Windows 7, and you do not have Ubuntu on that box.

What do you want us to tell you?

---

### Post by grahammechanical on 2014-08-18
Did you resize your Windows partitions? Did you use Windows utilities? The boot repair report is saying that the sizes of your partitions do not match the partition size information stored in the boot sector.

sda2 = Windows 7

> According to the info in the boot sector, sda2 starts 
                       at sector 206848. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       145407999 sectors, but according to the info from 
                       fdisk, it has 204799 sectors.

Something similar is said about sda 3 and sda 4. It seems that your partitions are smaller than they should be. And then there is this:

> 1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown [COLOR=#AA22FF]type [/COLOR]OS.

Windows not detected by os-prober on sda2.

There are supposed to be 2 Windows OS but Windows 7 on sda2 is not detected. Does Windows 7 still exist? Or has the partition been messed up requiring a re-install of Windows 7?

Regards.

---

### Post by coffeecat on 2014-08-18
Several points:

Perhaps you can't boot into Windows because you've installed grub4dos? I presume you have installed grub4dos because I see that you have /grldr in sda1, your Windows 7 boot partition. If you have installed grub4dos, why? If you install Ubuntu as a dual-boot, it will install the grub bootloader and set up a boot menu which will allow you to boot into either Ubuntu or Windows.

Another very important point. In this part of your boot info:

```
Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63         2,047         1,985  42 SFS
/dev/sda2               2,048       206,847       204,800  42 SFS
/dev/sda3             206,848   145,614,847   145,408,000  42 SFS
/dev/sda4         145,614,848   976,771,119   831,156,272  42 SFS

```

The "SFS" against all your partitions means that you have set up a dynamic disk. Dynamic Disk is a Microsoft proprietary logical volume system that only works with Windows. You cannot install Ubuntu to a dynamic disk. It is possible that the anomalies in the partitions that grahammechanical refers to are because of these being dynamic partitions.

Also - your intended Ubuntu partition is formatted with the Microsoft filesystem NTFS. You can't install Ubuntu to NTFS. The installer would convert that to ext4 and anyway, you won't be able to install Ubuntu to sda3 because of the dynamic disk situation. And you need to consider that Ubuntu usually has a separate swap partition.

It sounds as though you have plunged into preparing your hard drive without fully researching what to do. We can help you. A few questions.

What exactly is the nature of your problem booting into Windows? What happens? Are you in a position to be able to create a new install of Windows? If so, would you be willing to do that? Would you be able to back up your data on your Greenland partition, or have you already?

The reason I ask these questions is that with the complication of needing to convert your dynamic disk back to basic, your Windows booting problem, and whatever complication grub4dos might introduce, it might be quicker and easier to start afresh.

---

### Post by Mark Phelps on 2014-08-18
You won't be able to do anything with Linux until you convert your Dynamic Disks back to Basic Drives -- and to do that, you'll need to boot from a Windows filesystem repair disk.  You might be able to do this using either EASUS Partition Master or Minitool Partition Wizard -- both of which are downloadable Windows filesystems utilities.  But, while the paid versions do the filesystem conversion, I don't know if the free ones will.

Also, when done, you will have the 4-partition maximum on your hard drive, which means you STILL will not be able to install Linux because that is the maximum number of partitions you can have.  You will then need to decide what partition you can live without in order to remove it to create empty space for Linux.

---


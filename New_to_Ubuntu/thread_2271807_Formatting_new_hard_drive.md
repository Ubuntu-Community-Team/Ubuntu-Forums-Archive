---
title: "Formatting new hard drive"
date: 2015-04-01
forum: New to Ubuntu
---

### Post by dave6 on 2015-04-01
Hi all
Got a new 3tb drive today, it says Toshiba on the box and disc but it is in fact a Hitachi HDS5C3030BLE630 acording to ubuntu Disk Utility.  not that it matters what make it is.
But for the life of me I can not get it to format this drive, I have had this problem with this utility before and had been told to get some other software to do the same job, but I forget.

What would or could you recommend ?

Thanks 
Dave

PS, I need to format it in win NTFS for storing photographs on

---

### Post by oldfred on 2015-04-01
You have to partition first.
And since over 2TiB you have to use gpt partitioning.
If you will ever install an operating system on drive you may want to allocate 300 to 500MB as an efi partition at beginning of drive for UEFI boot. That is only required for newer computers, but can be difficult to add later when drive has lots of data.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by sudodus on 2015-04-01
Why do you want the NTFS file system:

- Because you are dual booting with Windows?
- Because you want to move the drive and connect it to a Windows computer?

It is best to create NTFS in Windows (but it is possible also in the linux GUI program ***gparted***).

I would use the GUID partition table, GPT, for a 3 TB drive. Then it is possible to create one single partition. If you use the old MSDOS partition table, you are limited to 2 TB partition size.

See the following link

[http://www.thegeekstuff.com/2012/08/2tb-gtp-parted/](http://www.thegeekstuff.com/2012/08/2tb-gtp-parted/) but I would use ***gparted*** instead of the text program parted (as described in the link).
[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by dave6 on 2015-04-01
> **sudodus said:**
> Why do you want the NTFS file system:

- Because you are dual booting with Windows?
- Because you want to move the drive and connect it to a Windows computer?

It is best to create NTFS in Windows (but it is possible also in the linux GUI program ***gparted***).

I would use the GUID partition table, GPT, for a 3 TB drive. Then it is possible to create one single partition. If you use the old MSDOS partition table, you are limited to 2 TB partition size.

See the following link

[http://www.thegeekstuff.com/2012/08/2tb-gtp-parted/](http://www.thegeekstuff.com/2012/08/2tb-gtp-parted/) but I would use ***gparted*** instead of the text program parted (as described in the link).
[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]
Why do I want the NTFS file system. Simple this hard drive is being plugged into a win7 computer via a USB docking port to backup 1.7tb of RAW files which the all singing all dancing photoshop can read, "I don't think much of photo-sh-t" it does run a lot faster than gimp which I also use along with Serif photoplus, and a few others.

I read the link, don't under stand it. but, !*** gparted*** rings a bell ?

How do I install it on ubuntu 12.04 64bit

Dave

gparted, have it downloaded and tryed to format the drive but it show errors, so I doing no more with this thing: enough is enough I quit

Dave

---

### Post by QIII on 2015-04-01
If you were to tell us what the errors were, we be able to provide assistance.

---

### Post by Bashing-om on 2015-04-01
dave6 : ^^^

Take a look at the tool gdisk - for large GPT disks.
See:
[http://ubuntuforums.org/showthread.php?t=2224130&page=2&p=13023988#post13023988](http://ubuntuforums.org/showthread.php?t=2224130&page=2&p=13023988#post13023988)
oldfred's post #17 in particular.

[INDENT][INDENT]quitters never win
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-04-01
Is this an internal drive, an external drive with its own connections or a drive you put into your own USB case?

May be best to format when connected as an internal drive. Some external drives have proprietary bits and some cases do not work with large drives and/or do not work with newer USB3 ports. If a case check specs.

---

### Post by sudodus on 2015-04-02
> **dave6 said:**
> Why do I want the NTFS file system. Simple this hard drive is being plugged into a win7 computer via a USB docking port to backup 1.7tb of RAW files which the all singing all dancing photoshop can read, "I don't think much of photo-sh-t" it does run a lot faster than gimp which I also use along with Serif photoplus, and a few others.

I read the link, don't under stand it. but, !*** gparted*** rings a bell ?
The link explains that you need a GUID partition table, GPT, if you want one big partition in a 3 TB drive. But you need not use the text interface. My idea was to use 1. Windows, or 2. gparted (if Windows is not available for you).> 
How do I install it on ubuntu 12.04 64bit

Dave

> **dave6 said:**
> gparted, have it downloaded and tryed to format the drive but it show errors, so I doing no more with this thing: enough is enough I quit

Dave

> **oldfred said:**
> Is this an internal drive, an external drive with its own connections or a drive you put into your own USB case?

May be best to format when connected as an internal drive. Some external drives have proprietary bits and some cases do not work with large drives and/or do not work with newer USB3 ports. If a case check specs.

You have Windows. I suggest that you use Windows the create the Windows file system NTFS :-)

If that does not work, I would agree with oldfred, that the problem might be the connection (assuming it is connected via USB). Would it be possible to connect the drive directly to an internal SATA port in a desktop computer or workstation, or via an eSATA port?

You should also make sure, that the power supply is sufficient for the drive and it's casing to work properly.

---

### Post by Siddhartha_Kashyap on 2015-04-04
I use a Linux distro called PARTED MAGIC to edit partitions. It can create both ext4 and NTFS partitions. i dont even have to install it, it boots from CD

---


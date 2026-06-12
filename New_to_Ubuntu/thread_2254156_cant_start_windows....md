---
title: "cant start windows..."
date: 2014-11-25
forum: New to Ubuntu
---

### Post by ispotopsi on 2014-11-25
I deleted my efi partition and now nothing is working
[http://paste.ubuntu.com/9234197/Thx](http://paste.ubuntu.com/9234197/Thx) for helping

---

### Post by grahammechanical on 2014-11-25
Your Ubuntu pastebin link does not exist either. Some information about the hardware and operating systems on that machine would be helpful, as well. 

You included Thx as part of the URL to the pastbin page.

> No OS has been found on this computer.

Ubuntu is not installed on either of the 2 hard drives. None of the partitions are Linux partitions. 

With Windows 8 pre-installed we need to follow the advice here.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by ispotopsi on 2014-11-25
[http://paste.ubuntu.com/9234197/](http://paste.ubuntu.com/9234197/)
Here the working link...
I deleted the linux partition and merged it to the windows partition and want to work with windows only.

---

### Post by yancek on 2014-11-25
The EFI partition usually contains both the windows/Linux files needed to boot in UEFI mode so if you deleted it...?  Your boot repair output shows sda2 as a FAT32 partition which is what the EFI partition usually is but no files are shown for windows or Ubuntu.  You have windows code in the master boot record of sdb and a window partition on that drive.  Do you have windows 8 on the 1TB drive, what's on the 500GB drive?  Multiple installs of windows?

---

### Post by ispotopsi on 2014-11-25
Only on the 250 gb drive is a windows installation

---

### Post by sotiris2 on 2014-11-25
Do you have any windows 8 media? Either a recovery disk or installation disk? A friend with windows 8 could also make you one. See [url=http://www.fixedbyvonnie.com/2013/06/how-to-create-a-windows-8-recovery-usb-flash-drive-in-5-minutes/#.VHT2FKClCw0]here[/code] for an example. Deleting the efi partition was a very very bad move :(

---

### Post by ispotopsi on 2014-11-25
Is the win 8.1 test iso alao working?

---

### Post by oldfred on 2014-11-25
With parted & gparted the boot flag sets the very long GUID that determines which partition is the efi partition.
It looks like you set boot flag on 3 partitions.

>  Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       616,447       614,400 [COLOR=#ff0000]EFI[/COLOR] System partition
/dev/sda2         616,448       821,247       204,800 Data partition (Windows/Linux)
/dev/sda4       1,083,392   488,394,751   487,311,360 [COLOR=#ff0000]EFI[/COLOR] System partition
/dev/sda5     488,394,752   488,396,799         2,048 [COLOR=#ff0000]EFI [/COLOR]System partition



With both UEFI and BIOS only one partition per device or hard drive can have boot flag.

In another place it says sda2 is labeled as the efi partition. So remove boot flags from sda1, sda3 & sda5 and add boot flag to sda2 only.
Script sometimes does not show efi boot files if partition not correctly flagged as the efi partition.
If you look in sda2, do you see /efi/Microsoft/boot folders?

---


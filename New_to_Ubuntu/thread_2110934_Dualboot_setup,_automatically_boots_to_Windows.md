---
title: "Dualboot setup, automatically boots to Windows"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by dempa on 2013-01-31
I have a dualboot setup with Ubuntu and Windows 7. I installed Windows 7 first on drive C:, then installed Ubuntu on D. I switched the default boot device to the D drive, however I am not prompted with an OS selection. Instead, it goes directly to Windows 7. I've tried reinstalling multiple times, even using different distros (tried mint as well, same result).

I'll post specs/screen captures when I get home.

---

### Post by Impavidus on 2013-01-31
Are those C and D drives separate disks (drives in Linux parlance) or separate partitions on the same disk (drives in Windows parlance)?

---

### Post by omeomi on 2013-01-31
> **dempa said:**
> I switched the default boot device to the D drive

Do you mean in the BIOS or did you install the bootloader on this drive during Ubuntu installation?

---

### Post by Mark Phelps on 2013-01-31
The "C:" and "D:" designations used in Windows, while they say drives, actually mean partitions, not physical drives.

The only way you can install Ubuntu to a Windows partition is using Wubi -- which creates a virtual filesystem INSIDE the Windows partition.  But, in this install, Windows still does the booting and adds an entry to its OS selection menu.

So, before anyone tells you to reinstall GRUB, you need to confirm that this was a Wubi installation (by looking for a root.disk file in your "D:" partition) and if that is the case, do NOT reinstall GRUB as that will only make matters worse.

---

### Post by dempa on 2013-02-04
I decided I'm going to format everything in order to make it work. What order should I install? I have 3 drives (physical drives), labeled C:, D:, and V:,

I'd like to have both my windows installation and my Ubuntu partition on C, since it's a solid state drive (128 GB). Is it more wise to format and install Linux first, then windows or the other way around? I know that if I do Linux first, I'll have trouble accessing grub after the windows install. If I do windows first, the whole drive will be formatted to NTFS, leaving no room to format ext3/4 for Ubuntu. Help?

---

### Post by henrx on 2013-02-04
you have to format the partition NTFS so linux can install it's boot mode properly.  Restart again and then on boot you should get the options.  Update your BIOS.

---

### Post by henrx on 2013-02-04
SOrry - formaat into FAT - not NTFS.  or google it - i forgot.  ;)

---

### Post by Mark Phelps on 2013-02-04
Your comments are mixing two very different forms of installing Ubuntu:
1) Wubi -- installs INSIDE an existing Windows NTFS partition
2) Regular -- requires creating an Ext4 filesystem partition and installing to that.

> **dempa said:**
> I decided I'm going to format everything in order to make it work. What order should I install? I have 3 drives (physical drives), labeled C:, D:, and V:,
Linux does NOT use drive letters.  When you install using Wubi, you install INSIDE an existing NTFS partition -- which has a drive letter in Windows -- but does not in Linux.

> I'd like to have both my windows installation and my Ubuntu partition on C, since it's a solid state drive (128 GB).
"C" is NOT a drive (even though Windows calls it this); instead, it is a Partition -- which is part of a drive. A partition can take up an entire Drive, but it would be better HERE to refer to it as a partition.
>  Is it more wise to format and install Linux first, then windows or the other way around? 
When you install Ubuntu using Wubi, you do NOT format. So, if you want Ubuntu installed INSIDE C, D, or V, there is no formatting to be done.
> I know that if I do Linux first, I'll have trouble accessing grub after the windows install. True, but you just then boot from the Ubuntu LiveCD or LiveUSB and reinstall GRUB.
> If I do windows first, the whole drive will be formatted to NTFS, leaving no room to format ext3/4 for Ubuntu. Help?True, but after you install Windows, just use the Win7 Disk Management utility to shrink it down to make room for Ubuntu.  Then, when you boot from the Ubuntu LiveCD/LiveUSB, choose the "something else" option to install to the unallocated space.

---


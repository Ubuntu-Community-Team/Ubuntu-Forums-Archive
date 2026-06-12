---
title: "Partitioning a 64GB Sandisk Extreme USB3 for Live USB use w/ persistence."
date: 2015-10-03
forum: New to Ubuntu
---

### Post by VpNKBQLjz0 on 2015-10-03
Hey. So I have one of [these.]("https://www.sandisk.com/home/usb-flash/extreme-usb") In 64GB.

Basically I want the device partitioned into 2 or so parts.

1 ~6GB part for the Live Ubuntu partition (with persistence)
1 part of free space in NTFS for Windows usage.

I've tied so many methods in getting this to work.. It's not a problem at all, **unless I want to get _persistence_ working...**

I've tried programs like [LiLi]("http://www.linuxliveusb.com/"), [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and [UNetbootin]("https://unetbootin.github.io/"). All of which allow setting persistence within the app.
None of them could properly format the drive during the 'creation' process because they all want to format the drive into FAT32 (the USB is too big). In the end none of them would cause the USB to boot in UEFI mode.
[Rufus]("https://rufus.akeo.ie/") did work (formatting in FAT32 Large) but then it has no option within the app to set persistence... so I can't save any settings/changes/files etc.

I've tried so many different ways of doing this:
Partitioning a part of the drive within GParted as 'ext4' and setting it as 'casper-rw' etc. and then adding the boot flags.
Using the first 3 above linked applications to try and make a bootable USB with persistence.
Making a 6GB partition for the Linux boot files and the persistence file and then trying all of the previous steps with that.
Using Unetbootin (within Linux and Windows) to do the above.

Nothing works. Persistence is never enabled upon boot in UEFI... Whyyyyyy?
I need to be able to save my files, downloaded drivers. etc. etc.

Please give me a hand.

---

### Post by yancek on 2015-10-03
I'm not sure what you mean by "None of them could properly format the drive during the 'creation' process because they all want to format the drive into FAT32".  Surely you don't expect software that is created for the specific purpose of making a bootable flash drive to give you options to make multiple partitions.  You would have to do that beforehand and if you have an Ubuntu or any Linux CD with GParted, create the first partition the size you want as an ntfs so it can be read/written to on both Linux and windows.  You would then use unetbootin or some other software to install your system to the flash on the second partition.  I used unetbootin to do this last week and it works fine.  You would need to select persistence when you put your Linux on the second partition but you are limited by FAT32 as it will be a casper-rw 'file' and files are limited to 4GB.  You need the first partition ntfs because windows is only able to read the first partition of a flash drive.  So you can make changes to your Ubuntu system and add some software, etc. but any data you want to share between systems will need to be on the first/ntfs partition.

I don't use UEFI so I have no idea how this will work with it.

---

### Post by VpNKBQLjz0 on 2015-10-03
Hi and thanks for the reply!

I don't expect those programs to give me the option to partition my USB drive. However it would be nice if any of those programs could bother to tell me that my drive is too big to format into FAT32. Instead all 3 of those first programs I mentioned simply 'said'' they were formatting the drive, and yet none of them did at all. Rufus was the only program that told me that the drive was too big to use traditional FAT32 and that if I used NTFS or exFAT that neither of them were bootable filesystems for Linux. So it left me with the option of FAT32 (Large).

I already did exactly what you suggested. Except I did it the other way around because I figured it would be a bit 'safer' to make the ***first*** partition the one with the Linux files on it (and set to FAT32) and then the rest of the USB as NTFS storage.
Thanks very much for the clarification as to why my unmentioned issue of Windows 10 not being able to format or mount the NTFS partition (after the FAT32 one) was occurring.

I'll try it the other way around!

[COLOR=#ff0000]**EDIT: It didn't work.**[/COLOR] When I change system settings in Linux and then reboot, they aren't saved. They are destroyed upon reboots.
The USB boots fine into Linux however, and the NTFS partition is readily usable in Windows. So I am almost the whole way there.

---

### Post by oldfred on 2015-10-03
I do not use live installer, but boot ISO from grub. Or with my 32 & 64GB flash drives have full Ubuntu installs.

But Windows will only read the first partition. So you must have your NTFS as first.
If you want UEFI boot, then installer must be in a FAT32 partition. I do not think making first partition FAT32 and also sharing with Windows would be good. UEFI will boot from a FAT32 with boot flag that is not first partition.

If you only want UEFI, not BIOS you do not even have to use installer. Installer formats partition, extracts ISO and adds BIOS based boot loader. 
So you can format NTFS, FAT32 with boot flag & any other partitions you want. And use any extraction tool you want to extract ISO to FAT32 partition.

Not sure if persistence works with UEFI, but you can add it as a boot parameter in BIOS boot, so I would think it would work if you add it as a boot paramater in grub. Most instructions show editing syslinux boot files to add parameter, but UEFI boots with grub, so you have to edit the grub.cfg in the installer.

[http://ubuntuforums.org/showthread.php?t=2259682](http://ubuntuforums.org/showthread.php?t=2259682)
[https://help.ubuntu.com/community/mkusb#Persistent_live_systems](https://help.ubuntu.com/community/mkusb#Persistent_live_systems)

---

### Post by sudodus on 2015-10-03
You can use mkusb. It works with large pendrives. I have a 128 GB pendrive, and it can be formatted automatically in a suitable way. You select the percentage to use for persistance (the third partition, a casper-rw partition with ext4 for persistence) and the rest of the drive space available will be used for the first partition with FAT32 for booting and for exchange of data with Windows.

(The second partition contains a cloned copy of the ISO9660 file system of the ISO file.)

See these links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[install mkusb](https://help.ubuntu.com/community/mkusb/gui)
[Persistent live systems](https://help.ubuntu.com/community/mkusb#Persistent_live_systems)

---


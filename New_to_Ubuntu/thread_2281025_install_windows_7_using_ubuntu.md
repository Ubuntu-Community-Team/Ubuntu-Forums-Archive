---
title: "install windows 7 using ubuntu"
date: 2015-06-03
forum: New to Ubuntu
---

### Post by jonah8 on 2015-06-03
I just finished my pc build. I have a product code for windows 7 and a disk but no disk drive to read it. The only usb drive I have available is 2GBs (super old) so I downloaded ubuntu and planned on then downloading windows 7 using ubuntu. again, I have NO optical disk drive (cd,dvd,etc.) and my only usb drive is too small to fit windows boot on. however I have two hard drives, one with ubuntu installed and the other completely blank. I want to be able to boot windows 7 from the blank hard drive, so I formatted it as NTFS and extracted the windows 7 iso file onto it. then i changed the boot flag in terminal using fdisk. however when i try to boot from it after leaving the bios menu my computer displays a black screen with a flashing underscore in the top left corner of the screen ( I assume this is what happens when you boot from something that is not bootable). I have never made a hard drive into a boot disk and maybe this isnt even possible? Hopefully I am just missing something in the process of turning it into a boot disk. any help is appreciated, thanks!

---

### Post by grahammechanical on 2015-06-03
I do not think that extracting an ISO image to a hard disk is the same as installing an OS to the hard disk. For a start that hard disk lacks a Windows boot loader. When we use the Ubuntu boot loader (Grub) to load Windows it looks for a Windows boot loader and then hands over control to the Windows boot loader.

What you need to research is running an ISO image from a partition on the hard disk and directing the installer to install Windows to other partitions on the same hard disk or a different hard disk.

This is how it would be done on Ubuntu with a Ubuntu ISO image. It could also work with this Windows 7 ISO image. Maybe.

[http://askubuntu.com/questions/340156/install-ubuntu-from-iso-image-directly-from-hard-disk-of-a-system-running-linux](http://askubuntu.com/questions/340156/install-ubuntu-from-iso-image-directly-from-hard-disk-of-a-system-running-linux)

Regards.

---

### Post by jonah8 on 2015-06-03
The reason i extracted the iso to my hard drive was that I was hoping i could replace the windows 7 instalation disc with reading it directly from the hard drive since i have no disc drive. It doesn’t seem like it will work so far though.

---

### Post by BBQdave on 2015-06-04
Way back with Apple osX (10.4) I would partition my drive (2 partitions) one would have a copy of the osX ISO and then I would install to the other partition. After installation, I then used the partition with the osX ISO for data storage (wiped the ISO).

A new thumb drive for install, is inexpensive too :)

---

### Post by yancek on 2015-06-04
The method described at the link below should work.  I used this method to put windows 10 extracted iso on an ntfs partition of a hard drive and followed the steps to boot it.  It did boot and start the installation.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by oldfred on 2015-06-04
You say new system, so probably UEFI with CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

Did you install Ubuntu in BIOS or UEFI mode?
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And then are you installing Windows in UEFI or BIOS mode. Windows 8 can be installed in either mode, but you have to move some efi files around on drive for Windows 7 to boot in UEFI mode. And then installer drive has to be FAT32 formatted so UEFI can read it.

  How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

---

### Post by VMC on 2015-06-04
> **jonah8 said:**
> ...The only usb drive I have available is _**2GBs**_ ...

Guys, this is all the OP has. So far, the only viable option is to find a loop method as grahammechanical has suggested. The usb options would work if he had a larger USB drive.

---

### Post by yancek on 2015-06-04
> Guys, this is all the OP has. So far, the only viable option is to find a  loop method as grahammechanical has suggested. The usb options would  work if he had a larger USB drive.         

No.  He specifically states in the initial post that he also has two hard drives although he doesn't mention their sizes.  He could use the method at the link I posted to extract the windows 7 iso, copy it to an ntfs formatted partition large enough to hold it, then create a boot entry in the Ubuntu grub.cfg menu to boot and install it.  This is apparently what he tried initially but didn't do it correctly so it didn't boot.  The 2GB flash drive isn't going to help and I don't see any need for it.

---

### Post by leunam12 on 2015-06-04
Is buying an external DVD drive not an option? You can get a good one for less than $20.00 on ebay and they are pretty useful if you have a computer with no optical drive. But I understand that when you are on a strict budget, spending an extra 15.00 it's a lot. I don't know if this is your case but I have been there many times. Good luck!

---

### Post by MartyBuntu on 2015-06-04
I'd assume if you had enough money to purchase a Windows license, you'd have at least $10 (or less) available for a USB flash drive...

---

### Post by gordintoronto on 2015-06-05
+1

---


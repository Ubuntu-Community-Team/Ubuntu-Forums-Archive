---
title: "Beginner Question: Dual boot windows 8"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by bigal337 on 2013-01-20
Hello, first time poster here!

Quick background: 
-build a pc last year
-now has 2 ssds, one Windows 8, and one Ubuntu 12.10

When I try loading windows 8 from grub,
I am getting the seemingly common 

"error: can't find command 'drivemap'
error: invalid EFI file path"

message.

I have scoured the internet for help, but nothing seems to be working. 


The furthest I've gotten was this:

[http://paste.ubuntu.com/1553949/](http://paste.ubuntu.com/1553949/)

which I got from Boot Repair.

Any and all help is appreciated!

Thanks!

-Al

---

### Post by oldfred on 2013-01-21
You have one install in BIOS (Windows) and one install in UEFI(ubuntu).
Both systems have to be installed in the same mode to let grub chain load from one to the other.

New systems have UEFI, but also have legacy BIOS and you can choose how to install when you install an operating system. Normally both Windows & Ubuntu will install based on how you boot flash drive installer. If booted UEFI then you install in UEFI mode, if booted in BIOS mode you install in BIOS mode.

UEFI is new and requires gpt partitioning. Windows only boots from gpt with UEFI. But gpt is only required for drives over 2TB, but is suggested for SSD by the Arch site. 
But BIOS/MBR partitioning is better understood as it only has been used since the first hard drive for an IBM PC in the '80s.

You need to reinstall Windows if you want both to be UEFI. But Ubuntu will work from BIOS boot with gpt drives, so you can convert install to BIOS boot. You will need a tiny 1MB unformatted partition anywhere on drive with the setting bios_grub.  Use gparted to create and then set flag. Do not format.

You probably can manually uninstall grub-efi and istall grub-pc but Boot-Repair can also do it for your.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by bigal337 on 2013-01-22
Thanks so much!

I used gparted and flagged the existing 1mb partition as UEFI_GRUB.

This time, grub repair detected it and reinstalled grub 2.

Windows 8 boots fine now!

Thanks again

-Al

---


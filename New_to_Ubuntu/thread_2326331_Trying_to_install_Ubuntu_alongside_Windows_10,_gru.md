---
title: "Trying to install Ubuntu alongside Windows 10, grub failed to install."
date: 2016-05-30
forum: New to Ubuntu
---

### Post by Korejora on 2016-05-30
When I try to install Ubuntu 16.04 it gives the error " The 'grub-efi-amd64-signed' package failed to install into / target/. Without the GRUB boot loader, the installed system will not boot. " and then quits. 

These are all the steps I can think of. Sorry if the information is incomplete or excessive. I don't understand some of the stuff going on. 
-- I have three data drives. I have Windows 10 installed on one, I have tried to install Ubuntu on the other, and the third one is just data. 
-- I put Ubuntu to install on a small USB stick using Startup Disk Creator in Ubuntu. 
-- When go into BIOS to boot to the USB stick, my computer labels the USB stick as UEFI. It does not label the other two possible boots (the CD drive and the Windows drive) as UEFI. Windows was installed from CD drive. 
-- When it installs it says that there is non-UEFI install on the disks, and asks is it OK to force UEFI install. I cannot figure out how to do not UEFI install so I say yes, force UEFI install. 
-- It says there is no operating system installed, so to avoid destroying Windows, I tell it to customize install Something Else. It says dev/sda/ is ntfs so I assume that is Windows and leave it alone. I tell it to remove all partitions on dev/sdb/ and put ext4 mount to "/" as primary partition on the start of dev/sdb/ and leave small amount of room for swap area. Then I put swap area as primary partition on the rest. For the boot loader at the bottom I tell it to put it on dev/sdb/. 
-- When I put in the username for the install, it suggests as computer name ' username-System-Product-Name-Invalid-entry-length-16-Fixed-up-to-11 '. 
-- While installing, near the end it gives the error " The 'grub-efi-amd64-signed' package failed to install into / target/. Without the GRUB boot loader, the installed system will not boot. " and then quits. 
-- Afterwards the BIOS boots are the same as before: USB stick, CD drive, Windows disk.  
-- When I try again to install it, it detects Ubuntu 16.04 as installed and finds the ext4 "/" and swap area.

Please advise!

---

### Post by grahammechanical on 2016-05-30
> suggests as computer name ' username-System-Product-Name-Invalid-entry-length-16-Fixed-up-to-11 '.

We edit that to give a name for the installation that is suitable for ourselves. 

Windows 10 will be installed in EFI mode and that means that Ubuntu must also be installed in EFI. To do that we load the live session in EFI mode.

It is quite likely that the hard disks have a GPT partitioning scheme. That means that when we install Ubuntu using the Something else option we need an efi_boot partition for the installer to put the Linux boot loader's efi boot files. So, it is my guess that the lack of an efi_boot partition is the reason for this happening

> 'grub-efi-amd64-signed' package failed to install into / target/.  Without the GRUB boot loader, the installed system will not boot. " and  then quits.

> if you use the manual partitioning  ("Something else"), the difference is that you will have to set the  /boot/efi mount point to the UEFI partition. And if there was not any  UEFI partition on your HDD, you first will have to create it (see the "[Creating an UEFI partition]("https://help.ubuntu.com/community/UEFI#Creating_an_UEFI_partition")" paragraph below).

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You could run a live session and install Boot Repair and then create a BootInfo summary report. You will get a URL to the location on the internet where the summary report will be stored. Paste the URL in this thread and we will see the situation for ourselves. Boot Repair will suggest a suitable repair option. You can choose to accept the repair or wait until some of us see the BootInfo summary report first. Your choice.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot Repair usually defaults to re-installing the Grub Boot loader into all hard disks. You may need to enter the Advance options to direct the installation of Grub on to sdb.

When we have only one hard disk and Windows 10 is on it. Then Windows 10 will have created an efi_boot partition for its efi boot files. In this case the Ubuntu installer will use the same partition for the Ubuntu efi boot files. This does not cause any problems.

Regards.

---

### Post by oldfred on 2016-05-30
Post link from Boot-Repair's Summary report.

It sounds like you may have installed Windows in BIOS mode which would be an MBR drive on sda. Which then had no ESP - efi system partition.
But grub only installs in UEFI mode to ESP on sda.

If new system with UEFI, you may want to re-install Windows in UEFI mode.
Or install Ubuntu in BIOS boot mode.
How you boot install media is then how it installs, for both Windows & Ubuntu.

---

### Post by Korejora on 2016-05-31
It is not a new system but back up is not difficult, so I have reinstalled Windows 10 from USB and now it is label UEFI in the boot order. 
After that I installed Ubuntu with the same steps (wipe dev/sdb, and put ext4 "/" and swap area, and tell boot loader to go on sdb). It did not complain about UEFI and it did not give errors installing grub. 
Ubuntu starts from grub OK now. 

Thank you friends for your help.

---

### Post by oldfred on 2016-05-31
Glad you got it working.

But if UEFI, even telling it to install to sdb does nothing. I watch install process and it will even say installing to sdb, but then actually installs grub to sda.
If you look at the ESP on sda you will have both a Microsoft folder & an Ubuntu folder for booting.

---

### Post by Korejora on 2016-06-01
It does seem like it installed to sda. Is there a way to have it install to sdb? Should I allocate room for /boot or some such when install Ubuntu? I do not want to lose grub if problems happen with sda drive or Windows installation.

---

### Post by oldfred on 2016-06-01
For your exact reason, I always create both the ESP & and a bios_grub as first partitions on drive. Then it can be configured for BIOS or UEFI boot.

I then copy /EFI/ubuntu folder from the ESP on sda to sdb's ESP and then copy again to /EFI/Boot and rename shimx64.efi to bootx64.efi
The bootx64.efi is a backup way or fallback default in UEFI. It also is how all external drives boot. But the use of shimx64.efi requires or is hard coded to find files in /EFI/ubuntu. 
No installing of boot loaders is required, but just copy files & folders.

You also can do a direct install of grub, but have to manually configure the grub.cfg in the ESP as a configfile to find the full grub.cfg in your install.

---


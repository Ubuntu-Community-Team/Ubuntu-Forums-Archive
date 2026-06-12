---
title: "Why do I need GRUB?"
date: 2015-02-28
forum: New to Ubuntu
---

### Post by numeric2 on 2015-02-28
Hi,
A newbie question; but, I will ask anyway. Why do I need GRUB? 
I just purchased a new Dell Inspiron 7000 i7 computer. I can boot the "try" Ubuntu 1404_2 usb device. I used Rufus to write the Ubuntu ISO file with UEFI boot stuff. Anyway it boots to Ubuntu without problems; I just had to set the BIOS so that the UEFI USB device was first on the list. 
  The installer, when activated, will try to install GRUB on the Windows disk drive boot sector. Since the BIOS scans for UEFI devices there is no need for GRUB, at least on this computer. Is there a way to put UEFI on the Ubuntu disk drive with out GRUB?
The Ubuntu disk drive is separate from the Windows disk drive.
Suggestions are welcome.

---

### Post by Mike_Walsh on 2015-02-28
>  [COLOR=#000000]Since the BIOS scans for UEFI devices there is no need for GRUB, at least on this computer...

[/COLOR]...[COLOR=#000000]The Ubuntu disk drive is separate from the Windows disk drive.[/COLOR]

Hallo, numeric2. 

It's a common misconception.

IF you only intend to run Ubuntu from the USB drive, then no, you won't need GRUB installed. However, if you decide you then want to 'dual-boot' with it alongside Windows, on the same machine (whether on one, OR two separate disk drives) then I would seriously advise allowing the installation of GRUB to proceed. 

Why?

Because if you don't install GRUB ( the** [COLOR=#ff0000]GR[/COLOR]**AND [COLOR=#ff0000]**U**[/COLOR]nified [COLOR=#ff0000]**B**[/COLOR]ootloader), then you will NEVER be able to boot into Ubuntu. This is because the Windows bootloader CANNOT see the **ext** (**2**, or **3**, or **4**) file systems that Ubuntu uses. GRUB, however, CAN read the Windows **NTFS** file systems; if it is allowed to install itself, then after running 'sudo grub-update' in the terminal, you will find that you have both Windows AND Ubuntu listed in GRUB, and it is simply a matter of selecting which O/S you wish to use...

I believe, if you are running the two O/S's from separate disk drives (not just separate partitions?), then you can simply choose to boot via the BIOS; but it WILL mean having to alter the boot order every time you wish to use one or the other. Having GRUB installed certainly makes it simpler, AND quicker.....but that's just my opinion.

Hope that helps to clear up ONE of the many 'Linux mysteries'. In this respect, at least, the 'vagaries' of UEFI don't come into it...at all.


Regards,

Mike. ;)

---

### Post by grahammechanical on 2015-02-28
2 hard disks? One for Windows and one for Ubuntu? Using the Something Else option it is possible to instruct the Ubuntu installer which hard disk and partition you want Ubuntu installed into. And also which drive Grub is to be installed on. Or even not to install Grub (I think). You would then have to enter the UEFI boot system to select which drive and which OS to load. I say this but I have no experience of UEFI.

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

> [COLOR=#252525][FONT=sans-serif]UEFI systems can access GPT disks and directly boot from them, simplifying things and allowing UEFI boot methods for Linux. Booting Linux from GPT disks on UEFI systems involves creation of an [/FONT][/COLOR][EFI System partition]("http://en.wikipedia.org/wiki/EFI_System_partition")[COLOR=#252525][FONT=sans-serif] (ESP), which contains UEFI applications such as _bootloaders_, operating system kernels, and utility software.[/FONT][/COLOR][SUP][[27]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-29")[/SUP][SUP][[28]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-30")[/SUP][SUP][[29]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-arch-uefi-loaders-31")[/SUP][COLOR=#252525][FONT=sans-serif]Such a setup is usually referred to as [/FONT][/COLOR]*UEFI-GPT, while ESP is recommended to be at least 512 MiB in size and formatted with a FAT32 filesystem for maximum compatibility.*

Installing Grub will let you load to the Ubuntu drive and then select either Ubuntu or Windows.

Regards.

---

### Post by numeric2 on 2015-02-28
> **Mike_Walsh said:**
> Hallo, numeric2. 

I believe, if you are running the two O/S's from separate disk drives (not just separate partitions?), then you can simply choose to boot via the BIOS; but it WILL mean having to alter the boot order every time you wish to use one or the other. Having GRUB installed certainly makes it simpler, AND quicker.....but that's just my opinion.


Thank you Mike for your reply. 
Yes I plan, for now, to run two OS's from separate drives. The Ubuntu OS is on an external USB 3 hard-drive. Windows 8.1 is using the internal (500 GB) hard-drive. Eventually, I will replace the internal one with a 1 TB hard-drive, or larger, and divide the drive into two main partitions. One for Windows 8.1 ( or maybe Win 10) and Ubuntu 14.04_2 LTE. However; this will void Dell's warranty. Also, the existing internal hard-drive is divided into several partitions for Windows 8.1, restore and other Dell stuff; no room left for Ubuntu :-(  
I agree with you, a one hard drive solution will require GRUB or equivalent.

Since the Ubuntu UEFI device is first on the BIOS list, then simply unplugging the Ubuntu drive should default to the next UEFI device (Windows boot manager) and boot to Windows. Hopefully avoiding having to enter the BIOS every time I want to switch OS's. If the UEFI list is "sticky" then reconnecting the Ubuntu USB drive should boot to Ubuntu. Maybe too many assumptions, it can't be that simple? I found out a long time ago, to what seems simple and logical, someone has spent a great deal of effort to avoid simple and logical.

---

### Post by oldfred on 2015-02-28
Are you booting in UEFI or BIOS mode? How you boot is how it installs:

 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by JeQhdMD on 2015-02-28
Perhaps the preferred way to run multiple OS's on a PC (as the IT depts do) is to run a HOST OS and one or more Guest OS's. 

This is done by deciding which OS to use as the machine HOST, and which OS's (windows, linux, MacOS, BSD) to run using a hyper-visor such as Virtual Box or VMware Player.   That way, no complex dual boot systems, multiple hdd's,  etc.    The modern PC should now have the OS booting from an SSD (for stability and speed (120gb minimum)).  The second internal HDD should be a high rpm hdd of 500 GB or more for data.

The main caveat to doing this is the PC has to have a fast processsor, ample ram, and the user is not looking for 3d hardware acceleration as used by gaming GPU's.  In other words, a professional working PC dedicated to things such as development, engineering, business acct, science, education and even general use.

---


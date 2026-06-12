---
title: "no idea EFI/UEFI problem installing ubuntu 16.04"
date: 2016-05-19
forum: New to Ubuntu
---

### Post by Pangestu_Apri_Seti on 2016-05-19
hello, im newbie and i need to fix my laptop as soon as possible :^o

in my case, i had existing windows 7 drive letter C D E, last night i try to install ubuntu 16.04-64, i didnt check about uefi problem..
i just install and delete my windows (not gonna use it again) on drive C and D [E for backup data still ntfs]
i make 3 partition when i install ubuntu /(root) about 80 /home about 160gb /swap about 16gb..
when i almost finish installation, theres error on session installing the grub 2 package..

and now, i just run my ubuntu via liveusb *try ubuntu :P cause my windows partition already gone *forever.. 

i already test this one, and the error said, 
[COLOR=#ff0000]The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?[/COLOR]
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

what should i do? :confused: explain to me like im 10 cause im really confused on this UEFI/EFI prob -_-

(sorry for my bad english)

i just finish the boot repair, hope its work..

[http://paste2.org/WpNEKsp7](http://paste2.org/WpNEKsp7)

---

### Post by mastablasta on 2016-05-19
does it boot after boot repair?

Also /swap partition is way too big unless you intend to fill up the ram to 15 GB and then hibernate the PC.

you can porbably also turn off EFI mode and install in normal mode or manually reconfigure the partitions.

---

### Post by grahammechanical on 2016-05-19
Once upon a time PC motherboards had what was called a BIOS boot system that used MBR partitioning which only allowed a maximum of 4 primary partitions, To have more than 4 partitions we needed to turn one of the allocated primary partitions into a special primary partition called an Extended partition. Inside the extended partition we could then create a large number of Logical partitions.

Then motherboards began to be produced that had a UEFI boot system and GPT partitioning. GPT allowed many primary partitions and did  away with the need of Extended & Logical partitions.

But at that time Microsoft was not installing its OS in the EFI install mode. So, you have a motherboard with a UEFI boot system but Windows 7 which is installed in BIOS/Legacy/Compatibility Support Mode (CSM).

Then you installed Ubuntu in EFI mode but you create 3 partitions which is fine for BIOS/Legacy/CSM + MBR partitioning but not fine for EFI mode + GPT partitioning. With EFI mode & GPT we need a efi_boot partition. Here are your choices

1) Leave the UEFI settings in EFI mode and load the Ubuntu installer in EFI mode and install Ubuntu in EFI (as you have done) but use the Erase disk & install Ubuntu option. Let the installer create the partitions it needs. Do you really need any other options?

2) Set the UEFI to BIOS/Legacy/CSM and load the Ubuntu installer in BIOS mode and install Ubuntu in BIOS and and select the Something Else option and make the partition selection as you have created those partitions.
> **Case when Ubuntu must be installed in UEFI mode**

Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]**if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. ** 
[/LIST]


Here is where it does matter

> if you use the manual partitioning ("Something else"), the difference is  that you will have to set the /boot/efi mount point to the UEFI  partition. And if there was not any UEFI partition on your HDD, you  first will have to create it (see the "[Creating an UEFI partition]("https://help.ubuntu.com/community/UEFI#Creating_an_UEFI_partition")" paragraph below).

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You are installing in EFI but without a efi_boot partition. And so, the install of Grub fails.

By the way, even with a BIOS boot system if we use GPT partitioning we will need a bios_boot partition. 

Regards.

---

### Post by oldfred on 2016-05-19
If you convert to UEFI, you need to also convert to gpt. That will erase your other NTFS data partitions. Be sure you have good backups.

Also you really need a Windows repair disk, if you are keeping NTFS partitions. NTFS periodically needs chkdsk which only can be run from Windows or Windows repair disk. Ubuntu schedules fsck periodically for ext4 partitions.

You can keep system as BIOS/MBR, but must always boot in BIOS mode.

You can convert to UEFI with gpt and as an alternative may be able to use the existing space that Windows 100MB boot partition as the ESP - efi system partition.

Then use gdisk to convert from MBR to gpt, reformat sda1 to FAT32 with boot flag to make it the ESP. Boot Boot-Repair in UEFI mode and have it uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI). It might be quicker to do a new install, but your data partitions would be erased, if converted during install to gpt.

       Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Besure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966](http://ubuntuforums.org/showthread.php?t=1718966)

Advantages are not huge:

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---


---
title: "Unable to boot any OS, please help!"
date: 2015-08-17
forum: New to Ubuntu
---

### Post by insunghan on 2015-08-17
Hi all, I am in desperate need of help as I have messed up my computer in trying to remove Ubuntu so I can install Ubuntu 15. When I boot my computer it is showing a grub rescue error. What had happened was I wanted to delete ONLY the SSD that had Ubuntu on it. I have Ubuntu installed on one SSD, Windows on another SSD and the bootloader installed on the SSD that had Ubuntu loaded.

I decided to use computer management in Windows 10 and formatted the second SSD that had Ubuntu on it. I thought that would of been a quick and easy way to format the SSD to install Ubuntu 15. But now when I boot my computer, it is now rendered unbootable saying error: unknown file system Grub Rescue with a prompt. I tried to change the boot order to the Windows SSD but it still says grub rescue error. It seems that the Windows boot loader is missing. Can anyone please help on how to restore the Windows boot loader? Thanks in advance for any help

Things that were tried so far:

-So I tried bootrec /fixmbr and the operation was completed successfully. Unfortunately the bootrec /fixboot option receives an error "Element not found". Both commands were done with a Windows 8 disc as I do not have a Windows 10 USB. The MS site doesn't have the option to download Windows 10 onto a USB stick on a macbook. They only provide an ISO file in which the macbook doesn't have an optical drive to put into.

-I have tried using the command bootrec /rebuildbcd which results in the same error "Element not found"

-I have tried using the boot repair from the Windows 8 disc. I think I made my problems even WORSE! The repair went under way and was successful. Unfortunately I am now getting a Windows boot loader error (probably because I tried using a Windows 8 repair on a Windows 10 install) "The boot selection failed because a required device is inaccessible"

Here are my system specs:

Antec 1200 / ASUS Z77 Sabertooth (BIOS v2104) / Ivy i7 3770 3.4 GHZ / Generic stock heatsink / Corsair Vengeance 8GB 1333 MHZ / SATA3 Samsung 830 SSD 250GB (Win10) / Samsung 840 SSD 120GB (Ubuntu) / 750GB HDD (Data Drive) Radeon HD 7850 2GB / Onboard Sound / Corsair CX750M / ASUS VW246H. Everything running at stock.

Samsung 830 (Windows 10)
Samsung 840 (Ubuntu w/grub bootloader)

Just remember I no longer have Ubuntu installed as I formatted the 840 in computer management in Windows which resulted in this problem that I have now. So now BOTH OSs have been rendered unbootable. I previously thought that the Windows boot loader was still on the 830 which is why I formatted the 840. I guess I was wrong. Please any help is appreciated!

Any help would be greatly appreciated.

---

### Post by howefield on 2015-08-17
Anything stopping you from using an Ubuntu 15.04 USB Live media to install Ubuntu back into the now formatted SSD (which will put grub back).

---

### Post by kansasnoob on 2015-08-17
I've not tried it with Windows 10 yet but Boot Repair would be able to fix that in all previous versions of Windows:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by insunghan on 2015-08-17
> **howefield said:**
> Anything stopping you from using an Ubuntu 15.04 USB Live media to install Ubuntu back into the now formatted SSD (which will put grub back).

I thought of that, unfortunately during the initial Ubuntu USB setup, it says no previous operating systems have been found on your computer which that isn't the case here. So I'm guessing if that is the case, then grub might not detect my Windows 10 install? Please get back to me on this if thats not the case. Thank you so much for your quick reply.

> **kansasnoob said:**
> I've not tried it with Windows 10 yet but  Boot Repair would be able to fix that in all previous versions of  Windows:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Unfortunately  I do not have another USB stick, the only other USB stick I have is the  one that has Ubuntu on it. I'm afraid to format that and lose any means to getting back to do any sort of repair.

---

### Post by dino99 on 2015-08-17
from the grub rescue screen, hit ctrl+alt+f2 to get a terminal. Then run:
> sudo blkid to get the strict device address; select the path of your ubuntu ssd (something like /dev/xxx), then you will be able to format it with 'gparted live', install ubuntu on it (manual choice= 'something else' option) and finally install grub on it.

---

### Post by insunghan on 2015-08-17
> **dino99 said:**
> from the grub rescue screen, hit ctrl+alt+f2 to get a terminal. Then run:
 to get the strict device address; select the path of your ubuntu ssd (something like /dev/xxx), then you will be able to format it with 'gparted live', install ubuntu on it (manual choice= 'something else' option) and finally install grub on it.

It looks like I have made my problems much worse. I used the Windows 8 repair only for it to SUCCEED! The Windows 8 disc repaired "something". Now when I try and boot I get a windows boot loader error instead of the grub rescue error. I think I might of put a Windows 8 boot loader onto a Windows 10 install. The grub error no longer shows so now i can't use your suggestion! ARGH!

---

### Post by oldfred on 2015-08-17
My suggestion is to always have a current version live installer or Windows repair flash drive for every system you install. So you should have a Windows installer or repair flash drive so you can run Windows repairs. And Ubuntu live installer to both install or if necessary repair Ubuntu.

And I do like to make sure with two drives that installs are totally separate, or you can boot either install without other drive.

Did  you install in UEFI or BIOS boot mode?
Your Z77 should have both as a boot option. And if changed then system in other boot mode would not boot.

Boot-Repair can install a BIOS type Windows boot, if system is in BIOS mode.
It cannot install Windows boot files with BIOS or UEFI as those are Windows and copyrighted, so if missing or major repairs you have to have Windows repair tools.

If you have Ubuntu on flash drive, even if previous version (if not past support), you should be able to boot in either BIOS or UEFI mode and run Boot-Repair. The Summary Report gives lots of useful info on configuration and is good just to have, if you have multiple installs or multiple drives.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by insunghan on 2015-08-17
> **oldfred said:**
> My suggestion is to always have a current  version live installer or Windows repair flash drive for every system  you install. So you should have a Windows installer or repair flash  drive so you can run Windows repairs. And Ubuntu live installer to both  install or if necessary repair Ubuntu.



I manage to get a Windows 10 USB stick, unfortunately the boot repair option did not work and the computer is still rendered unbootable. Even more confusing, the Windows 10 USB stick is reading my computer as a Windows 7 machine! My only assumption as to why this is happening is because I tried to use the boot repair option from a Windows 8 disc. Even when I try and do a clean install the USB stick is reading my machine as a Windows 7 machine. Any help is appreciated.

EDIT1: I'm afraid I might have to resort to do a full format, my only concern right now is will a full format also delete the corrupted boot loader/mbr?

---

### Post by oldfred on 2015-08-18
Some Windows repairs/updates do not rewrite the MBR as it assumes you still have a Windows boot loader in the MBR. But a new install always overwrites the MBR and erases grub2's boot loader, so you have to have Ubuntu live installer to reinstall grub to MBR after Windows updates or repairs.

If reinstalling Windows and you have Linux in a logical partition, be sure to backup partition table. Windows does not correctly see Linux partitions and often "forgets" to write the sda5 or sda6 Linux partition back to partition table. Data is still there and testdisk or parted rescue can often restore it if not otherwise changed. If UEFI install less of an issue.

Only for MBR(msdos) partitions. For UEFI use gdisk which has different commands.
       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

    Do not restore if you edit partitions after backup.

---


---
title: "Grub doesn't find Ubuntu Install"
date: 2017-07-05
forum: New to Ubuntu
---

### Post by swifty162 on 2017-07-05
I booted up Ubuntu from a USB (downloaded from the site yesterday), I initially encountered the graphics issue from the link below, but was able to overcome it by enabling "nomodeset".

[https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

Following this I tried Ubuntu without installing, from there I successfully installed Ubuntu in place of Windows 10 which was previously there (I had no data on the laptop and did not wish to keep Windows).  However, on booting up I am only able to access the USB Grub menu, without the USB there are no bootable devices.  If I try to repeat the steps and install the software notifies me that Ubuntu is already installed (as it would if Windows were installed).


I have tried boot-repair and part way through received the message "The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag). Do you want to continue?".  I continued with the process but alas nothing changed.

Also - the HDD is listed as an SD card (as a newbie I am not sure if that is normal).

Any help is appreciated!

---

### Post by oldfred on 2017-07-05
Some of the very low cost systems use a SD or MMC card as the drive.

What brand/model system?

You must have newer UEFI system if you have booted installer in UEFI mode. How you boot installer is then how it installs. This link shows the difference between the first screen of UEFI boot (grub) and BIOS (purple menu).

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

New UEFI hardware has two (really 3) boot modes, UEFI or BIOS. And UEFI can be with Secure boot on.
And if you install in UEFI mode, but have system set to boot in BIOS it will not work. Or vice versa.

And generally the 35 year old BIOS uses the old MBR partitioning. And newer UEFI uses gpt partitioning. Windows requires you to use gpt with UEFI installs. And all systems preinstalled from Vendor are UEFI/gpt.

But with UEFI boot on gpt you must have the ESP - efi system partition which is FAT32 with boot flag.
With Ubuntu, but not Windows you can use gpt partitioning and still boot in BIOS mode, but must have a tiny 1 or 2MB unformatted partition with bios_grub flag. When manually partitioning a new drive I generally add both the ESP & bios_grub, but now install in UEFI mode. But could convert to BIOS boot if desired.

See link below for more info.

---

### Post by JonPaul on 2017-07-05
Have you tried switching from UEFI to legacy in your bios settings? 

When I installed Ubuntu instead of Windows 8 on my Acer E1-571 about 3 years ago I couldn't get it to work on UEFI. I think things may have improved since then...

if you mean your hard disk is listed as /dev/sda it doesn't mean it is an SD card. sd used to stand for SCSI Disk and the 'a' meant the first one.

---

### Post by swifty162 on 2017-07-06
Thank you both for your help.  The issue was that the system was booting in UEFI mode but the install was through the BIOS.  I reinstalled via UEFI and all is working well now!

---


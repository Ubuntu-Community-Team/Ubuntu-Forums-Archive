---
title: "[Dual Boot, Boot Repair] GRUB2 menu not showing Windows7"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by jaymax on 2013-04-28
Hi.

So I used to be pretty good with Linux, but that was twenty years ago... Trying to get going again without learning everything from the insides out.

I have installed Windows 7, and then Ubuntu.  The Win-7 install seemed to have created two small partitions at the start of the disk.  I assume one or both of these was for the Windows bootloader, which I assumed I no longer required - I think I selected one of them for GRUB2 in the early part of the Ubuntu install process.

I have tried using Boot-Repair on both the MBR and GRUB - but I can't get a GRUB menu to display which includes Windows.

[http://paste.ubuntu.com/5613904](http://paste.ubuntu.com/5613904) is my latest go at it...  Some way through it states: "Windows not detected by os-prober on sda3." but it is there with all the normal Win-7 structure etc.  Right at the end it says:

"Quantity of real Windows: 1 
WinSE in sda3 /mnt/boot-sav/sda3/ may need repair.
/mnt/boot-sav/sda3/bootmgr may need repair. 
grub-install (GRUB) 2.00-13ubuntu3,grub-install (GRUB) 2."

Partitions I created were ~64GB for Windows-7 primary, ~64GB for ubuntu primary, Something like ~512GB for user (my) data, and a swap of about 16GB at the back of the disk.  As I mentioned, Win install created two ~100MB partitions at the front, which I might have buggered, but what would Windows want with them if I'm booting via GRUB?

Confused; thank you in advance for any help.

--
ubuntu 13.4; windows-7-ultimate; 8GB; UEFI motherboard

---

### Post by 0N3 on 2013-04-28
Have you tried grub customizer?

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by 0N3 on 2013-04-28
Under general settings you can look for other operating systems see if it picks it up

---

### Post by jaymax on 2013-04-29
Just installed it, the option was already ticked, but saved and restarted anyhow.  No change - still no Windows entry in boot menu :-(

---

### Post by Mark Phelps on 2013-04-29
> **jaymax said:**
> ...
I have installed Windows 7, and then Ubuntu.  The Win-7 install seemed to have created two small partitions at the start of the disk.  I assume one or both of these was for the Windows bootloader, which I assumed I no longer required - I think I selected one of them for GRUB2 in the early part of the Ubuntu install process.

You assumed wrong -- that smaller partition most likely contained the Windows boot loader files -- which, it looks like, are gone now, which is why os_prober can't see Windows.

You will need to RESTORE the windows boot loader files.  You may be able to do this with Boot-Repair:
[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by oldfred on 2013-04-29
Even worse, this is a UEFI system and the fat32 partition that was first was the efi partition with all the boot files.

You have Windows on a gpt partitioned drive and it only boots by UEFI and has its boot files in the efi partition.
Windows only boots from gpt with UEFI, Or from MBR with BIOS.
Ubuntu will boot from gpt or MBR(msdos) with BIOS or from gpt with UEFI.

You can only have one efi partition per gpt partitioned drive.
(even on MBR you can only have one primary partition with the boot flag)
Gparted confused the boot flag a bit by using the boot flag to indicate the efi partition with gpt partitioning. It is not really the same as the boot flag in BIOS/MBR which means the Windows partition to boot from.

Format sda1 as FAT32 and use gparted to add boot flag or make it the efi partition.
Remove boot flags from sda3 & sda4.
Use Boot-Repair to convert Ubuntu from BIOS boot to UEFI boot by uninstalling grub-pc and installing grub-efi.

Not 100% sure on how to totally recover the Windows boot files if you do not have a backup of the efi partition.
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Windows does have this, but you also need a BCD in the efi partition and it has other support files also.

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.


 All linux distro installers (Ubuntu included) assume EFISYS partition to be mounted at /boot/efi.

After you update Ubuntu to UEFI mode the efi partition should have these:
      
 /boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/BOOT/bootx64.efi

But you also need this and all the other files it has normally.
      
 /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi

---

### Post by jaymax on 2013-04-30
Thanks Mark & oldfred.

I should have mentioned that I didn't have any critical data, so recovery rather then start-over was just in forlorn hope of saving some time re-re-re-starting from scratch.  I had obviously managed to make quite a mess of things trying to make it work :-/

With a bit of digging on the MS side, it seems that Win7-64bit-upgrade disks have some issues with installing to gpt (on UEFI).  Even though GPT is supposed to be mandatory for that config, a lot of folk have ended up installing to MBR (using MS diskpart in the early stages of install to convert their HDD from GPT to MBR).  A couple of people alluded to BIOS settings allowing them to install onto GPT; and while I still haven't wrapped my head around UEFI, I just went through my BIOS and turned anything storage related that offered 'Legacy' and/or 'UEFI' to be UEFI only, or UEFI first, or whatever...

Then reinstalled Windows no problem, used Gparted to shrink the C:\ partition and shuffle it to the right a bit, created additional small partitions for \boot (somewhere previously Boot Repair had said something and pulling /boot to the front of the disk possibly being a good idea) and bios_grub (whatever that is?) after the EFI and windows reserved partitions, installed ubuntu and all is good in the world.  Currently I have dual-boot from the UEFI BIOS boot menu, and the EFI (as suggested) includes both MS and Grub boot stuff.  I might see if I can make GRUB also offer boot selection, but it's working at the moment and so I'm reluctant to poke around too much...

NB: First subsequent Win7 start ran a disk check on C:, but found no errors... 

Thanks again, tomorrow I shall see if VirtualBox wants to play nice with my windows partition.  What fun shall we have then, lol.

---

### Post by jaymax on 2013-04-30
:-( My thread tools / post edit don't seem to have any option to let me change thread title to [SOLVED]...

:-) Edit / _Advanced_ / change dropdown

---

### Post by oldfred on 2013-04-30
Boot-Repair should add correct chain entries to UEFI Windows.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---


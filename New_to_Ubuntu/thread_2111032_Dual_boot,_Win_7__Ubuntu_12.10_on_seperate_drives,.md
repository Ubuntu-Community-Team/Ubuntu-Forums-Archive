---
title: "Dual boot, Win 7 / Ubuntu 12.10 on seperate drives, BCD is blank"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by sogrey on 2013-01-31
I searched for an answer, but was unable to find...
 
1. I have little knowledge of Ubuntu, I am using 12.10 (I tried Ubuntu several years ago).
2. I built a computer, ufei bios, multiple hard drives, SSD and two sata 6. Windows 7 is on the SSD, (drive C:), Ubuntu is on a sata 6 (drive F:). Through sheer luck, I got Ubuntu installed on a seperate drive without wiping windows.
 
Question: BCD in windows is blank, I am not getting the option to dual boot. I can go to bios and boot the ubuntu drive but would really like the screen with the choice on which OS to boot. I can set the boot drive to Ubuntu and grub gives me the option for either OS. (Again, sheer luck on getting that to work). I would prefer the traditional screen after post offeringme the choice on OS.
 
Any suggestions?
 
Thanks in advance.

---

### Post by oldfred on 2013-02-02
With a UEFI/BIOS system you can install either Windows or Ubuntu in UEFI or in BIOS mode. And both must be in the same mode to dual boot.
If Ubuntu is in a different mode than Windows, Boot-Repair can convert if drive is partitioned with gpt.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

If UEFI mode:
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---


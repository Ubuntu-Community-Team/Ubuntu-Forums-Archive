---
title: "&quot;invalid efi path&quot; after upgrading BIOS"
date: 2023-11-17
forum: New to Ubuntu
---

### Post by gabrielbergoc on 2023-11-17
Hey, so I'm upgrading my processor from a Ryzen 3 2200G to a Ryzen 7 5700G, and according to the manufacturer of my mobo (ASRock A320M-HD), I had to upgrade the BIOS version (P5.40) to the last version (P7.30) to use my new processor, so I followed the instructions on their website ([https://www.asrock.com/mb/AMD/A320M-HD/index.br.asp#BIOS](https://www.asrock.com/mb/AMD/A320M-HD/index.br.asp#BIOS) -> upgraded first to P7.00 then to P7.30), but now when I try to boot Windows 10, it shows the following message (translated from portuguese):

"Partition type defined as 0x7
error: cannot find command 'drivemap';
error: invalid EFI file path.

Press any key to continue..."

When I press any key, I'm thrown back to the grub menu.
I could only boot Ubuntu in recovery mode, then I ran Boot-Repair, and the output was this: [https://paste.ubuntu.com/p/XKpCb4K5pn/](https://paste.ubuntu.com/p/XKpCb4K5pn/)

What should I do?

---

### Post by oldfred on 2023-11-17
Microsoft has required vendors to install Windows in UEFI boot mode with gpt partitioning since 2012 and release of Windows 8.
You have the old BIOS boot mode with MBR partitioning for Windows.
Ubuntu lets you install in UEFI boot mode to old MBR partitioning & probably should not.

Best thing would be to totally reinstall Windows in UEFI mode with conversion to gpt partitioning. That will totally erase entire hard drive(s), so good backups required. And then reinstall Ubuntu in UEFI mode to gpt drive.

UEFI firmware update probably reset everything to defaults. 
You may be able to reset default boot mode to BIOS/Legacy/CSM to get system to work for now.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Note that NVMe drive is a  lot faster than HDD. Often best to have operating system on fastest drive and data that is less used on slower drive.
Backups then need to be to other devices.

---

### Post by MAFoElffen on 2023-11-18
Just a driveby... I notice two things from from errors.
> Partition type defined as 0x7
0x7 denotes type NTFS partiton type... All the disks, including the NVMe are MBR instead of GPT. Grub2 is installed as both Legacy and UEFI. Windows is installed as Legacy.

The machine was booted as UEFI boot mode. When he upgraded his BIOS, the default setting is UEFI, not legacy.

One note about Windows. Although recommended that all Win 10 is installed as UEFI, Win 7 was Legacy Boot. if you upgraded Win 7 to Win 8, then Win 8 to Win 10, through the the free upgrade path... Then you ended up with Win 10 as Legacy boot on an MBR partitioned drive. 

It is dead-ended there, because you will need GPT and UEFI to get to Win11... I mean you could boot as Legacy, chroot into Ubuntu and reinstall Grub as legacy, and be back up and running, but... Still, you are limited and your hands tied with how it is currently setup.

It is in your best interest to dig into regedit to document your product activation code... backup all your data, and reinstalled both Windows and Ubuntu on GPT partitioned disks.   

Now would be the best time to do that.

---

### Post by tea for one on 2023-11-18
Together with oldfred and MAFoElffen, the priority should be to backup all your personal data.
Then install Ubuntu 22.04 and Windows 10/11 in UEFI mode with GPT.
As you have two disks, you may want to consider each OS on a separate disk?

I noticed the following line in the boot-repair report:-
Line 246 - '/etc/grub.d/proxifiedScripts/linux' | /etc/grub.d/bin/grubcfg_proxy "+'Ubuntu'~5883d3b2f14da566495dd987a70d7ba3
Did you install grub-customizer?

---


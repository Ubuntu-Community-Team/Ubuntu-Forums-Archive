---
title: "Windows 8 UEFI Cant Install Ubuntu"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by TarasTyshchenko on 2013-01-08
Hi guys I just bought new laptop, it came preinstalled with Windows 8 Pro. Its Toshiba Satellite p850 - 31l but I cant install any OS to replace Windows. I read about it and disabled the secure boot, still nothing happens when I put Ubuntu on disk into the drive it straight loads into Windows 8. How can I completely get rid of windows 8 and install Ubuntu. Or am I screwed and stuck with this shiny tiles icons now ?

---

### Post by oldfred on 2013-01-08
Welcome to the forums.

I would not get rid of Windows 8, some computers have issues without it. If you do remove it best to make a full backup first. And the recovery set of DVD. Also backup efi partition as that has the Windows boot files. A few systems can only get back into the UEFI menu from Windows (bug in UEFI)

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings, also some systems cannot get to UEFI menu with quick boot on unless Windows is booted first.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
Use Windows to shrink the Windows partition. If you just want / (root) & swap, just install into the unallocated space. Otherwise use Something Else or manual install and create partitions. You install grub to the efi partition if you have booted with installed in UEFI mode. 

You will need boot repair to fix the chainload to Windows.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by TarasTyshchenko on 2013-01-09
Hey thanks for the advice mate, it seems a bit to complex and there is no easy way to do this. I cant risk of playing about with things I have no experience with on a very expensive laptop lol. But cheers anyways

---

### Post by grahammechanical on 2013-01-09
>  still nothing happens when I put Ubuntu on disk into the drive it straight loads into Windows 8. 

Did you do the simple and easy step of setting the machine to look on the DVD drive or USB port for an OS to boot before it looked on the hard drive? It is called changing the boot order.

Could that be the reason it boots into Windows 8?

---


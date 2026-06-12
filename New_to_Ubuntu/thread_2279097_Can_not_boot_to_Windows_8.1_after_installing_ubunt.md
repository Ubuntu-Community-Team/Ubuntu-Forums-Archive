---
title: "Can not boot to Windows 8.1 after installing ubuntu 15.04"
date: 2015-05-20
forum: New to Ubuntu
---

### Post by tomvpham80 on 2015-05-20
Hi all
I have trouble boot to Windows 8.1 after installing ubuntu 15.04
When I go to ubuntu terminal and type: fdisk -l. It shows windows OS still there.

```
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000ce182

Device     Boot      Start        End   Sectors   Size Id Type
/dev/sda1  *          2048     718847    716800   350M  7 HPFS/NTFS/exFAT
/dev/sda2           718848  981549055 980830208 467.7G  7 HPFS/NTFS/exFAT
/dev/sda3        981551102 1953523711 971972610 463.5G  5 Extended
/dev/sda5        981551104 1020610559  39059456  18.6G 82 Linux swap / Solaris
/dev/sda6       1020612608 1953523711 932911104 444.9G 83 Linux
```

I make mistake did not turn off fast boot and secure boot during installation and It may cause the problem?
Anyone can help me with this problem? Thanks a lot.

Tom


Problem solved after update and reboot. Thanks all

---

### Post by RobGoss on 2015-05-21
I have the same problem on one of my machines you will have to go in to your bio's and change the boot sequences in order to boot into Windows 8 them, change it back if you want to boot up Linux. The only way you would be able to fit this is remove the new install of Ubuntu and do a fresh install in the correct order. I left mines like that because I don't use Windows any more.

---

### Post by Allen McBride on 2015-05-21
I have the same operating systems. By default when I start up I get the GRUB menu, which has a Windows option but it doesn't work. So to get to Windows I press F12 on startup and that takes me to the UEFI menu. The options are the same, but from there the Windows option actually works.

---

### Post by jones quest on 2015-05-21
You could try turning off fastboot and secure boot. Then fixing the boot loader, grub, with boot repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).

---

### Post by grahammechanical on 2015-05-21
Perhaps it is time to visit this wiki page

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It is not necessary to turn secure boot off but this is necessary

> In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").

And then there is this

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]


A machine with Windows 8 pre-install does indeed have Windows 8 installed in EFI mode. So, was Ubuntu also installed in EFI mode? That is the question.

Regards.

---


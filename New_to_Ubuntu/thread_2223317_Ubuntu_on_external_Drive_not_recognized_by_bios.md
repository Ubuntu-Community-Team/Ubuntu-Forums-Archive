---
title: "Ubuntu on external Drive not recognized by bios"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by Steve99321 on 2014-05-10
Hey,

i try to set up my dual boot system with Windows 8 (SSD), so i installed ubuntu 14.04 on an external HDD with USB 3.0.
I already have lots of files on this HDD (NTFS-Format) which i dont want to remove. This is why i added partitions by myself and since i am an absolute linux beginner i have no idea if it was enough to just install ubuntu on ext4 + swap. 
Long story short: When i set the bios to boot from this HDD, nothing but a blinking cursor is to see. 
Did i miss something within the setup? How do i make the bios recognize the GRUB within Ubuntu?

Thanks for your time guys

---

### Post by Cbhihe on 2014-05-10
Steve,
please describe your partitioning setup precisely with /dev/sd[x][n] labels.

An excellent read that will help you a lot for anything related to the GRUB boot loader is here:
    [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
A must browse. It is 17 pages long, includes lots of screen captures and has a good index.
Inside this document are more pointers if you want more and dies to get deeper in the matter of GRUB.
hth.

---

### Post by oldfred on 2014-05-10
Also what video card/chip do you have. 
If nVidia you may need nomodeset or others may need different parameters.

Is Windows installed in UEFI or BIOS boot mode?

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by Steve99321 on 2014-05-14
> **Cbhihe said:**
> Steve,
please describe your partitioning setup precisely with /dev/sd[x][n] labels.

An excellent read that will help you a lot for anything related to the GRUB boot loader is here:
    [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
A must browse. It is 17 pages long, includes lots of screen captures and has a good index.
Inside this document are more pointers if you want more and dies to get deeper in the matter of GRUB.
hth.



I read some pages of it, but for now i better tried to get the system running by reinstalling ubuntu, and it succeded.

 I partitioned it like
**sdc1  **UEFI Bootloader
**sdc2  **/ with ext4
**sdc3  **/home with ext4
**sdc4  **swap
**sdc5  **old ntfs partition

But after booting Windows 8 again the old problem occurs again.
So somehow Windows or its bootloader seem to change something with the UEFI bootloader or bios configuration.

I dont have any experience beside choosing the boot device inside the bios, so i dont know where the error comes from.

> **oldfred said:**
> [COLOR=#000000]Also what video card/chip do you have. [/COLOR]
[COLOR=#000000]If nVidia you may need nomodeset or others may need different parameters.[/COLOR]
[U]Further information about my notebook:
[/U]**[SIZE=2]Asus N56VZ-S4066H[/SIZE]**

[SIZE=2][COLOR=#000000][FONT=Segoe UI]**CPU:   ** Intel Core i7 3610QM
[/FONT][/COLOR][COLOR=#000000][FONT=Segoe UI]**Chipset:    **Mobile Intel HM76 Express
[/FONT][/COLOR][COLOR=#000000][FONT=Segoe UI]**Graphics:   **Intel HD Graphics 4000 + NVIDIA GeForce GT 650M[/FONT][/COLOR][/SIZE]

---

### Post by oldfred on 2014-05-14
May be best to see all details.
If Windows is UEFI and Ubuntu BIOS that would explain having to boot from UEFI/BIOS.
Also one or the other could reset default video mode as you have both Intel & nVidia.

       Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Steve99321 on 2014-05-14
> **oldfred said:**
> May be best to see all details.
If Windows is UEFI and Ubuntu BIOS that would explain having to boot from UEFI/BIOS.
Also one or the other could reset default video mode as you have both Intel & nVidia.

The extern HDD has an EFI-Partition as well. So acutally i dont know what the problem is if i choose to boot the UEFI 



I dont know the kind of bootloader windows has, but there is 350MB MB Boot partition on my SSD where Windows 8 is installed. I read that Windows 8 fast boot mode could cause trouble, so i turned that off.

The UEFI Bootloader (150MB partition) is installed on the extern HDD to start Ubuntu. If i connect my HDD, i can choose to start this UEFI-Partition in the BIOS. So only if i remove the secondary option to start windows from my SSD, i come to the blinking cursor screen, otherwise Windows 8 boots.

> **oldfred said:**
> 


       Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I guess my graphic isn't the problem for now. Ubuntu is working after installation, just gets trouble after one windows start. 
But anyway, when i used my secondary monitor over hdmi connection, it needs the nvidia card, which caused some graphic bugs (like only partly refreshing windows on the screen). But i guess standard graphics are provided by the Intel HD 4000.

---

### Post by oldfred on 2014-05-14
Oldfred forgot to post link when he said to see all details. 
Post link from BootInfo report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Steve99321 on 2014-05-15
Ok here i have generated the BootInfo report:

[http://paste.ubuntu.com/7467485/](http://paste.ubuntu.com/7467485/)

---

### Post by oldfred on 2014-05-15
You have Windows installed in sda with MBR partitioning and BIOS boot.
You have Ubuntu installed in sdc with gpt partitioning and UEFI boot.

The two boot modes are not compatible and once you start booting in one mode you cannot change to another mode. Or you cannot dual boot from grub menu and only from UEFI menu. And some systems require you to turn on UEFI or turn off CSM/BIOS, others autoswitch but may have to change some settings.

Windows and Ubuntu only boot from MBR partitioned drives with BIOS.
Windows only boots from gpt with UEFI.
Ubuntu can boot from gpt with UEFI or BIOS. If you want to dual boot from grub menu you can easily convert UEFI install in sdc to BIOS boot. You have to add anywhere on the drive a tiny 1 or 2MB unformatted partition with the bios_grub flag. You have to use live installer & gparted to add that. Then you can use Boot-Repair to uninstall grub-efi and install grub-pc. I would leave efi partition for future use since system is also UEFI capable.

---


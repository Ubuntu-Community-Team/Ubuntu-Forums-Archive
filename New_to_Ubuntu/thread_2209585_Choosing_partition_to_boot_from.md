---
title: "Choosing partition to boot from"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by nunecas123 on 2014-03-06
Is there any possible way of choosing a partition to boot from on the BIOS? It's because I can only choose the disks, but not the partitions. I would like to have multiple systems on an external hard drive but I can't seem to do that.

Should I run sudo update-grub on the system which the multiple distros?

I wanted a graphical way, just like in Mac's.

Thank you in advance.

---

### Post by Mark Phelps on 2014-03-06
> Is there any possible way of choosing a partition to boot from on the BIOS?No --in the BIOS, all you can do is set which physical drive is scanned first for a boot loader, not individual partitions.

I have heard about something called BURG -- which claims to be a graphical version of GRUB.

---

### Post by oldfred on 2014-03-06
Grub is a boot manager as well as boot loader for Ubuntu. 
It lets you choose which system to boot, but it is not graphical just simple menu.

If a new UEFI system you can use rEFInd which is graphical. It started from UEFI for Macs.
 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

### Post by grahammechanical on 2014-03-06
I have multiple installs of Ubuntu and its flavours on two hard disks and I get a boot menu which lets me select what OS to install. I can also use the BIOS to chose which hard disk I should be booting into by default.

If you have Ubuntu installed on sda and that has the BIOS boot priority then load into Ubuntu and run

```
sudo update-grub
sudo grub-install /dev/sda
```

That should do what you want.

If you have another install in sdb then load into that installation from the Grub boot menu and run

```
sudo update-grub
sudo grub-install /dev/sdb
```

Then when you use the BIOS to make sdb the boot priority you will get the Grub boot menu of the Linux version on sdb.

One version of Grub will be installed into the MBR of sda and another version of Grub will be installed in the MBR of sdb but both menus should show a list of all the operating system on both hard disks because that is the way that Grub works.

This is what I see when I run update-grub

> Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-16-generic
Found initrd image: /boot/initrd.img-3.13.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found Windows 8 (loader) on /dev/sda1
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sda2
Found Ubuntu Trusty Tahr (development branch) (14.04) on /dev/sda5
Found Ubuntu 13.10 (13.10) on /dev/sda6
Found Ubuntu 13.10 (13.10) on /dev/sda7
Found Ubuntu Trusty Tahr (development branch) (14.04) on /dev/sda9
Found Ubuntu 13.04 (13.04) on /dev/sdb1
Found Ubuntu Trusty Tahr (development branch) (14.04) on /dev/sdb5
Found Ubuntu Trusty Tahr (development branch) (14.04) on /dev/sdb9
done




And that gives me a Grub boot menu that lets me boot different versions of Ubuntu on two hard disk and also Windows 8 developer pre-edition.

Regards.

---

### Post by nunecas123 on 2014-03-07
How can I install [COLOR=#000000]rEFInd? Sorry, I'm such a newbie when it comes to these things... I don't want to mess up my system.[/COLOR]

---

### Post by oldfred on 2014-03-07
Is system a new UEFI system, rEFInd is only for UEFI not BIOS?
BIOS boots from MBR, UEFI boots from an efi partition on gpt partitioned drives.
New meaning hardware is new as UEFI is new update to the 35 year old BIOS type system. And motherboard must have that built in.

---

### Post by nunecas123 on 2014-03-07
After a quick look on Google about UEFI and your insight, I finally got to know that I can't do it. I'll stick with BURG anyway.

Thanks!

---


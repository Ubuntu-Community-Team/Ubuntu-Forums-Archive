---
title: "Boot Failure, boot device was rejected by the Secure Boot feature"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by McBeef on 2013-04-05
This is my first time trying to install ubuntu. I am running a Toshiba Qosmio X875-Q7390 running Windows 8, firmware 6.30 (the latest). I had downloaded the ubuntu 64 bit iso file and used unetbootin to create a bootable USB drive. The flash drive is a SanDisk Titanium 4GB Cruzer. When I try to boot into the drive I get this error:

> Boot failure: a proper digital signature was not found.

One of the files on the selected boot device was rejected by the Secure Boot feature.

What should I do?

---

### Post by N00bn on 2013-04-05
Google is your friend.[URL="http://www.eightforums.com/tutorials/17058-secure-boot-enable-disable-uefi.html"]

http://www.eightforums.com/tutorials/17058-secure-boot-enable-disable-uefi.html[/URL]

---

### Post by JimS on 2013-04-05
...
Today I successfully installed Ubuntu 12.10 and 
now I can dual-boot along with Win 8 on my new HP2000 laptop

Recommend viewing all 3 parts of "Practical UEFI Secure Boot" on YouTube
[http://www.youtube.com/watch?v=eAnlhkbMang](http://www.youtube.com/watch?v=eAnlhkbMang)

Then follow the Boot-repair instructions in 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
...

---

### Post by oldfred on 2013-04-07
Generally best to turn secure boot off to install. And turn off fast boot. Some systems only install in BIOS/CSM mode but Boot-Repair can convert, but you cannot boot a secure boot system in BIOS mode unless you turn it off. But still better to install in UEFI mode if you at all can.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by dougrm2 on 2014-01-17
Did you ever get ubuntu installed and running?  Which version(s)?  What works/doesn't?  I'm looking at a good deal for your type of machine but don't want to waste my time if ubuntu tanks too badly.

---


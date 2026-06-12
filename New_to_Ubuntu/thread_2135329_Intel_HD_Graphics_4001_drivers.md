---
title: "Intel HD Graphics 4001 drivers?"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by ginnyotte on 2013-04-13
I do not know how to get the latest drivers forve a Dell my graphics card?  I have a i17R-1316sLV 17-Inch Laptop with  Intel HD Graphics 4001 graphics card.  One of the games I want to play tells me thta I do not have adequate graphics; it worked when I had Windows on the same machine.

---

### Post by deadflowr on 2013-04-14
The drivers for intel are open-source only and come installed with the system already.
However, if you choose you can try the install the beta variants from here:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Note that these typically are very new and might junk up your system, so use at your own risk.

---

### Post by ginnyotte on 2013-04-14
why do some program report that I do not have updated drivers?  These programs ran under Windows 8, and ran under puppy linux.  Since converting the machine to Ubunu I can neither run those programs, or boot from my CD.  I go into my bios, nothing has changed...hit f12, choose boot from cd...nope.  Goes straight to hard drive.  Install programs that should run, they don't.  Even flash, which says is installed...won't run Amazon Prime instant videos.  I even try running that using wine, and try running my oteher programs using the Windows software under wine.  Since installing Ubuntu over Windows 8, obliterating Windows 8, I can neither boot froma CD nor run certain programs.  It is getting quite frustrating.

---

### Post by Mark Phelps on 2013-04-15
Windows and  Linux have very different drivers -- so stuff that relies on driver features could easily run in Windows while not running in Linux.  And, you can't install the Windows drivers in Linux; you have to get Linux drivers instead.  This is complicated by the fact that hardware suppliers rarely supply Linux drivers.

---

### Post by oldfred on 2013-04-15
Is this a new system that had Windows 8 pre-installed?
Then it had UEFI with secure boot.
Also is it an UltraBook with small SSD that is Intel SRT, but uses RAID. RAID causes issues.
And ULtraBooks have dual video which needs Bumblebee to work well.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

      
 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)

---

### Post by fantab on 2013-04-15
> **ginnyotte said:**
> why do some program report that I do not have updated drivers?  These programs ran under Windows 8, and ran under puppy linux.  Since converting the machine to Ubunu I can neither run those programs, or boot from my CD.  I go into my bios, nothing has changed...hit f12, choose boot from cd...nope.  Goes straight to hard drive.  Install programs that should run, they don't.  Even flash, which says is installed...won't run Amazon Prime instant videos.  I even try running that using wine, and try running my oteher programs using the Windows software under wine.  Since installing Ubuntu over Windows 8, obliterating Windows 8, I can neither boot froma CD nor run certain programs.  It is getting quite frustrating.

It is suggested that you should Dual-Boot until such time that you are comfortable with Ubuntu. Since you've already erased Windows, you can either opt to continue with Linux, without getting frustrated; OR re-install Win8 and then dual boot with Ubuntu.

If you can tell us:

What 'programs' you are trying to install in Ubuntu? and how?
What are you trying to boot from CD? [When there is nothing to boot from CD, or if the CD is not bootable then the BIOS boots from HDD].

perhaps we can help you.

---


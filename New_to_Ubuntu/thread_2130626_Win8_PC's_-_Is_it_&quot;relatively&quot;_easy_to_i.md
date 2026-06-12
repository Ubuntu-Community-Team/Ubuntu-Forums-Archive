---
title: "Win8 PC's - Is it &quot;relatively&quot; easy to install Ubuntu IF removing Windows??"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by GregA on 2013-03-30
Just curious if these steps can or will result in a "relatively" easy install of any Buntu Linux (Ubuntu, Ku, Lu, Xu, etc.) ,  , 

1.   Check out & purchase desktops and/or laptops with good track record in running Linux (research certified hardware on Ubuntu etc.)
2.   Update the UEFI to enable Legacy BIOS mode along with disabling secure boot.  Also, disable fast boot if that option is available in the setup routine.
3.   Boot into a Live CD or DVD or USB Flash-Stick and verify hardware compatibility.
4.   IF good on the above 3, use the Live media to install the Buntu distro by utilizing the entire drive (and thereby replacing Windows 8 entirely).

In other words, in the above situation, can average Windows users that don't require OR want to run a dual-boot, _expect a hassle-free, relatively painless install of Linux_?  

By the way, **my preferred way to obtain a Linux PC is pre-installed**  (e.g., buy a ZaReason or System 76 PC) . . . but the above may be a second-best alternative.

Am I basically on safe ground with these assumptions, . . . or am I missing something (such as, . . . is there a substantial down-side to running new hardware without UEFI/Secure boot enabled IF not running Windows) . . ??? 

Your thoughts much appreciated - thanks.

PS:   one other thought just occurred to me, I'm also assuming the "boot-order" will need changing in the Legacy UEDI/BIOS - just like it always has so Live media will start the system.

---

### Post by CamPsych on 2013-03-30
Hi. 
I am a newbie but this is exactly what I did on an Acer E1 531. A few hardware related issues that I am working through, but to this point, worked a treat.

---

### Post by kurt18947 on 2013-03-30
I believe the most recent releases - 13.04 & 12.04.2 - will boot with secure boot enabled.  I don't have any personal experience with it though.  If they will, it seems you could dual boot if you wish.  I find it useful to have a recent Windows version available in case I need to do something like hardware maintenance and Windows is the only option.

---

### Post by oldfred on 2013-03-30
There have been a couple of threads where users did just what you want. They erased Windows and installed Ubuntu. 
I generally suggest to dual boot as a few systems seem to have UEFI linked to Windows somehow and may have issues.
I would avoid the high end Ultrabooks. They have another small SSD drive that uses RAID which has to be removed. Also they use dual video Optimus which is not supported by nVidia although many use bumblebee successfully. 

 And I really like the poster a few weeks ago that said when he buys a  new laptop, he buys a better system, but with a hard drive. Then removes  Windows hard drive and puts it on the shelf in case he sells system  later. He then installs a SSD and Ubuntu. Best use of Windows hard drive  I have heard. :smile:

---

### Post by kurt18947 on 2013-04-01
> **oldfred said:**
> There have been a couple of threads where users did just what you want. They erased Windows and installed Ubuntu. 
I generally suggest to dual boot as a few systems seem to have UEFI linked to Windows somehow and may have issues.
I would avoid the high end Ultrabooks. They have another small SSD drive that uses RAID which has to be removed. Also they use dual video Optimus which is not supported by nVidia although many use bumblebee successfully. 

 And I really like the poster a few weeks ago that said when he buys a  new laptop, he buys a better system, but with a hard drive. Then removes  Windows hard drive and puts it on the shelf in case he sells system  later. He then installs a SSD and Ubuntu. Best use of Windows hard drive  I have heard. :smile:

I don't have a machine with UEFI/Secure Boot.  I wonder how the BIOS/Firmware/whatever on the mother board reacts when it sees a new 'hard drive' with no UEFI partition.  Will it refuse to boot anything that isn't Secure Boot approved?  Swapping out a hard drive to get rid of all that crap seems too simple.  Disable Secure Boot then swap out the hard drive?

---

### Post by oldfred on 2013-04-01
The new UEFI/BIOS has two or even three modes. You have UEFI with or without secure boot and you have CSM or the old BIOS. Only new UEFI systems with Windows 8 pre-installed currently have secure boot, but secure boot is part of the UEFI standard. And a user can turn it on or off.
  UEFI Compatibility Support Module (CSM)


So if installing to a blank drive you can install Ubuntu in UEFI mode with either secure boot on or off. Some systems only install with secure boot off, but then boot ok with it on.
But many other Linux systems have not yet implemented secure boot, but many now have UEFI boot and everyone has BIOS boot.

IF in UEFI mode you have to partition with gpt not MBR(msdos). Ubuntu will boot from gpt partitioned drives with either UEFI or BIOS. But with UEFI you have to have an efi partition at start of drive or with BIOS and gpt you have to have a 1MB unformatted bios_grub partition. 

If you partition with MBR, then you have to use BIOS/CSM to boot. And it can be difficult then to convert from one mode of booting to the other as it depends on drive partitioning.

---


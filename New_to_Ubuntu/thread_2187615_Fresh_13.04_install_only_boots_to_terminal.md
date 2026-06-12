---
title: "Fresh 13.04 install only boots to terminal"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by christallman14 on 2013-11-13
I just purchased an Acer Aspire V5-122P-0408 with the intention to put Ubuntu on it. I installed Ubuntu 13.04 (64 bit) via usb drive and the instillation went smoothly. However, now, when I go to boot the computer, it only boots in terminal mode. I have tried startx but that doesn't work, and I've tried updating it from the terminal. The update also went smooth, but that leads to a blank screen unresponsive boot, which is what lead me back to re-re installing of 13.04. I am at a loss here, has anybody else had this issue that knows how to solve it? Thanks!

---

### Post by fantab on 2013-11-13
Can you boot the ubuntu live USB in 'Try Ubuntu without installing' mode? Let us know.
Did "Acer Aspire V5-122P-0408" come with pre-installed Win8? What kind of Graphics do you have on board? Are you installing in UEFI or 'legacy' mode?
Tell us what all you did before you installed Ubuntu. Did you erase Windows? How did you managed the partitions? Are you dual-booting? What Ubuntu 32bit or 64bit?

---

### Post by Bucky Ball on 2013-11-13
Instead of 'startx' you want 'lightdm'

---

### Post by fantab on 2013-11-13
> **Bucky Ball said:**
> Instead of 'startx' you want 'lightdm'
+1. 
I missed that in OP's post.

---

### Post by christallman14 on 2013-11-13
It does the same thing when you "try Ubuntu without installing." It is running in UEFI mode. The laptop came with Windows 8 but I wiped it completely when I installed Ubuntu. According to TigerDirect.com, the computer has AMD Radeon HD 8210 graphics. To install Ubuntu I went through Windows 8 and set the computer to boot from the USB drive within windows. Then I used the Ubuntu installer to erase the hard drive and Install Ubuntu. It is the 64bit version. If I set the computer to Legacy vs. UEFI it will run Ubuntu from the flash drive, but when I try to boot from the hard drive off Legacy it states that there is no bootable device.

---

### Post by oldfred on 2013-11-13
Do you want UEFI boot or BIOS boot.
With Ubuntu you can boot from a gpt partitioned drive with either UEFI or BIOS.
Windows only boots from UEFI with gpt partitioning.
Both Ubuntu & Windows only boot with BIOS mode from MBR(msdos) partitioning. 

When you boot Ubuntu live installer it will offer from UEFI menu both UEFI booting or BIOS booting. And how you boot installer is the mode that it installs in.

This shows the first screen you get with either BIOS boot (purple screen) or UEFI boot with grub menu.
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Other Acer threads, mostly UEFI.
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

---


---
title: "Can't Install Ubuntu"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by DeadlyEvolution on 2012-08-20
Hello, I'm very interested in using Ubuntu 12.04 - I am currently running Windows 7 64-bit and I am on Ubuntu 12.04 via VirtualBox. I can get Ubuntu to install 100% perfectly on VirtualBox, but whenever I try to install it alongside Windows it just won't work. If I try using the WUBI.exe to install it that way it doesn't work. I set the hard drive size to 18GB (On my C:\ Drive) and I keep everything else default, it works fine up to the point where it asks me to reboot, when I reboot and actually try to get into/install Ubuntu it shows the Ubuntu 12.04 screen and the 4 dots. It loads for about 10-30 seconds and then brings me to a console screen where it says "Gave up waiting for root device" and under that it says "ALERT! /dev/disk/by-uuid/(Bunch of numbers/letters here) does not exist. Dropping to a shell!" And I can't do anything. If I hit CTRL+D or I type 'Exit' it just provides the same error alert. I can get into Ubuntu by using the live CD which I burned to a disc, but whenever I try to install Ubuntu using the disc it will NOT detect any of my hard drives. It shows connected to Internet with a green check-mark but the 'Has 4.5GB available space' has a black X and it won't let me continue. I tried using fdisk and a couple other methods online to figure out if the hard-drive is even detected by the system. And the only drive it shows is my disc drive. I have a 60GB SSD and a 1.5TB hard-drive.

System Specs:
Motherboard: GIGABYTE Z68X-UD4
Processor: Intel Core i7-2600K
Video Card: XFX Radeon HD 7970 Black Edition
Memory: 8GB DDR3
SSD: 60GB Chronos Deluxe
HDD: 1.5TB Western Digital Caviar

I'd love to get this issue sorted so if anyone can help it would be greatly appreciated.

Sidenote: I checked my BIOS to see if maybe my SATA mode wasn't set-up correctly, it's on IDE, I tried setting it to AHCI and the only other option is Raid(XHD) which I'm not using raid.


TL;DR
Gave up waiting for root device and under that it says ALERT!  /dev/disk/by-uuid/(Bunch of numbers/letters here) does not exist.  Dropping to a shell!
Hard-Drives not detected in live-cd

---

### Post by PGScooter on 2012-08-20
You might want to try the Alternate CD install. It is a bit slower but has more options and sometimes works for me when the normal cd doesn't.

---

### Post by DeadlyEvolution on 2012-08-20
> **PGScooter said:**
> You might want to try the Alternate CD install. It is a bit slower but has more options and sometimes works for me when the normal cd doesn't.

Fixed my issue by going into my BIOS and setting my gSata3 and eSata3 both to AHCI and also setting my default SATA mode from IDE to AHCI. On Ubuntu and running great! :D Thanks for the suggestion though

---

### Post by PGScooter on 2012-08-20
> **DeadlyEvolution said:**
> Fixed my issue by going into my BIOS and setting my gSata3 and eSata3 both to AHCI and also setting my default SATA mode from IDE to AHCI. On Ubuntu and running great! :D Thanks for the suggestion though

Good job figuring that out! I don't think I would have been able to solve that myself. Also thanks for posting back your solution. That's always good to see and will be useful to someone in the future. Enjoy and good luck!

---


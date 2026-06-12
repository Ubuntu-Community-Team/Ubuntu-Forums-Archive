---
title: "Select ubuntu in BIOS but Windows 8 pro boots instead."
date: 2013-05-09
forum: New to Ubuntu
---

### Post by Cylon1 on 2013-05-09
A little background first--
 
I'm using a Lenovo Yoga 13, i5 4 gigs ram 128 SSD Windows 8 Pro. No disk drive, no ethernet port-- yeah yeah I know... tethered to droid phone for internet and Ubuntu recognizes it w/o any extra drivers..

I had 12.04.2 installed and it worked GREAT. I loved it!
Until one time it completely melted down on me... It said failed to load directory "/".... I tried the built in recovery mode and it failed as well. :( 

I figured since I have to reinstall anyway, I may as well try version 13.04. It seemed to install normally, but after it asked me to reboot, it boots to Windows 8._** I select Ubuntu in my UEFI and it STILL goes to Windows 8**_. I can still boot up from the flash drive I used to install it. I have tried without the flash drive plugged in as well, it keeps going to Windows 8.

So I figured, hey maybe I should just roll back to 12.04.2 since it was working... Bad news there-- Grub2 failed to install. I tried several times, trying different tweaks like formatting over the previous installation to EXT4, then selecting that partition and installing Ubuntu there... it still gave me Grub failure errors. I tried resizing the partition, same. I tried making sure I set aside 4 gigs for swap, it always failed! 

So I tried 13.04 again, it installed flawlessly, no grub probem-- but it just WON'T boot-- _windows boots instead_!! I'm a newbie to Linux, but this is very discouraging. Mac OS seems to be getting slower and the power user features are nearly gone, and windows 8..well, I even tried to drink the cool-aid and still can't stomach that OS, so I'm hoping to get this back up and running asap!

Any ideas?? I really appreciate it!

Steven

---

### Post by sharke on 2013-05-09
Steven.
windows 8 can cause problems when dual booting with Linux.
The easiest solution is to go here [http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm](http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm) and follow instructions.
Cheers
Sharke

---

### Post by squakie on 2013-05-09
you should probably try running boot repair with just the default settings. Just install it while running a live session from your USB, then run it. Remember that for 12.04 (I'd go with 12.10) and 13.04, you must use the 64-bit version with UEFI.

---

### Post by fantab on 2013-05-09
Pre-installed Windows8 especially, come with a feature called "Secure Boot" which restricts other OS from booting and sometimes even installing. It has to be disabled first from BIOS. From version 12.04.2 however it is possible to boot Ubuntu with "Secure Boot" on but I am yet to meet users who have installed Ubuntu without hassels. Also Windows 8 pre-installed uses GPT partitioning instead of legacy 'DOS'. As pointed out, you must use 64bit Ubuntu to be able to boot from UEFI, AFAIK.

What you need is **[BOOT REPAIR]("https://help.ubuntu.com/community/Boot-Repair")** to fix that booting issues. After you install Boot Repair in Ubuntu LiveDVD/USB it will scan your computer and suggest "Recommended Repair", you should just run the recommended repair and that should fix your Boot issue. If you are still unable to fix it then try turning off the "Secure Boot". If you have further problems the post the output of _BootInfo Script_ (which is part of Boot Repair) here.

---


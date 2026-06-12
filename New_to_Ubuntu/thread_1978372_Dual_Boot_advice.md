---
title: "Dual Boot advice"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by JBudOne on 2012-05-11
Hey guys!

   I've been a long time Windows user, who has decided to recently swap over to Linux. I've dual booted my laptop with Ubuntu and Vista, but have just recently used gparted to resize my Windows partition to much smaller, and now can no longer boot into Windows. I've run `grub update-db` but even though it recognizes the Windows partition, it doesn't start up properly.

   Since my Windows partition is now probably broken, I was considering reinstalling Windows, and keeping my GRUB bootloader and Ubuntu distro still here. However I was talking to a friend of mine today, and he warned me that reinstalling Windows when I already have Grub/Ubuntu on my system could be a very dangerous and risky idea. He said that if I must go this route, I'd be better advised to reformat everything from scratch, then install Windows first and THEN Ubuntu next. The lazy part of me is starting to kick in, and I'm considering just sticking with Ubuntu as my only OS.

    My question is: is my friend right? Is it really so risky to reinstall Windows when I already have GRUB and Ubuntu loaded? And also, how safe is it for me to run a non-dual-booted system? I was mostly planning on keeping Windows as a backup, in case anything goes wrong with Linux, at any time I can still easily boot into Windows.

   Any tips, advice or insight into these things would be very helpful and much appreciated. Thank you!

---

### Post by Jacobonbuntu on 2012-05-11
> **JBudOne said:**
> Hey guys!

   I've been a long time Windows user, who has decided to recently swap over to Linux. I've dual booted my laptop with Ubuntu and Vista, but have just recently used gparted to resize my Windows partition to much smaller, and now can no longer boot into Windows. I've run `grub update-db` but even though it recognizes the Windows partition, it doesn't start up properly.

   Since my Windows partition is now probably broken, I was considering reinstalling Windows, and keeping my GRUB bootloader and Ubuntu distro still here. However I was talking to a friend of mine today, and he warned me that reinstalling Windows when I already have Grub/Ubuntu on my system could be a very dangerous and risky idea. He said that if I must go this route, I'd be better advised to reformat everything from scratch, then install Windows first and THEN Ubuntu next. The lazy part of me is starting to kick in, and I'm considering just sticking with Ubuntu as my only OS.

    My question is: is my friend right? Is it really so risky to reinstall Windows when I already have GRUB and Ubuntu loaded? And also, how safe is it for me to run a non-dual-booted system? I was mostly planning on keeping Windows as a backup, in case anything goes wrong with Linux, at any time I can still easily boot into Windows.

   Any tips, advice or insight into these things would be very helpful and much appreciated. Thank you!

Installing Windows *after* Ubuntu will certainly make Ubuntu unaccesible, unless you know special tricks. Indeed installing Ubuntu after Windows is the easyest way. If you can do without windows depends on what you need Windows for, and if you need to coöperate with people on some applications. Dual boot is normally not the best guarantee for avoiding problems, although I never had any. Since a year I do not dual boot anymore, and a Linux installation is less likely to fail than a Windows installation I guess, so the need for a "backup" is not bigger than with Windows. Apart from that; *if *Ubuntu will not start up, it is most likely a grub error, and in that case Windows will not start as well...

---

### Post by JBudOne on 2012-05-11
Jacobonbuntu,

   That makes sense. I guess the best course of action for me is to take my friend's advice; remove Windows entirely, give all of that allocated space to Ubuntu, and just use VirtualBox for any Windows-related stuff :)

---

### Post by oldfred on 2012-05-11
If your machine can handle VirtualBox or other virtual systems that can be a better way. If you do not have enough RAM it can make system slow all the time.

Older systems will work better with dual boot, but then you have the hassle of dual booting.

If you used gparted to resize Vista you usually  just need to repair the NTFS partition boot sector and run chkdsk. You need a Windows repairCD/USB or full install DVD.

You can easily reinstall grub2's boot loader to the MBR with a Ubuntu liveCD or several repairCDs.

oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---


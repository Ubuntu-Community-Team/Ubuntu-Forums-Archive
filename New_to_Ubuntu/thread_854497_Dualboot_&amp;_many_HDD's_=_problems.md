---
title: "Dualboot &amp; many HDD's = problems"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Primi on 2008-07-09
Hey,

Alright then. I tried to install Ubuntu 8.04 next to Windows XP, but all I get was suffer. First I couldn't boot from Live CD nor ALT. I always got errors like this:

ata03.01: revalidation failed (errno=-5) 
buffer I/O error on device df0, logical block 0
Sometimes there was ata5.01 or ata6.00

There is some Initramfs thing where you can write some commands.

I found quite many things which didn't work, but finally I found a post where ppl were talking about disabling floppydrive from BIOS. After doing that I get something like this:

42. 253121 .irq 18: nobody cared (try booting with the irqpoll option)
another same kind number-thing f884cb80 (usb_hod_irq+8x8/8x60 usborel
- -
Disabling IRQ a18
ata03.01: revalidation failed (errno=-5)

Well, back to searching some help. Found a thing about problem with Abit ip35 serie motherboards and they got it working when putting HDD's to last SATA -ports which are 5 and 6. After doing that it finally started installing ubuntu. Everything seems to be fine after installation, I can boot to windows and ubuntu and so on.

I shut down the computer and attached last 2 HHD's to my computer using ports 1 and 2 for them. I put the boot priority (BIOS) how it should be and I get GRUB error 22. BAH! Well, I was going to install GRUB again so I booted from live CD, or at least tried to. After loading bar I get BusyBox v1.1.3 (Deping 1:1.1.3-5ubuntu12) build in shell (ash) so I can't reinstall GRUB or do anything else. 

I have tried with different HDD and SATA -port combinations but couldn't get it working with anything else than plugging Windows and Ubuntu HDD's to 5 and 6 SATA -ports and removing other HDD's. Tried also put OS HDD's to 1 and 2 ports and other HDD's to some other ports and so many other combinations. Always I get this Busybox thing or some other errors.

I have Abit35 Pro, 4gb memory, 8800GT, Q6600, 4x HDD's which one is for Ubuntu and one for Windows, one is empty and one is NTFS with some music etc. files. DVD drive is some LG ATA/PATA/IDE or what is it called. 

I have been fighting with this problem 2 days for now. Lots of new information which makes my head dizzy. Always get one problem, after solving that I get another and so on. Can't think clearly today anymore so I finally tried post to this forum and ask help. Does anyone know what is the problem and how it can be solved.

I hope those error are written rightly and they are in right spot. As I said, I have got very confused with all this :) Sry about lack of english skills but I hope you understand.

Cheers,
Primi

---

### Post by Primi on 2008-07-10
I was thinking, should I change something from GRUB pr add some new lines there if I switch HDDs to another port or add new HDDs?

---

### Post by Levo on 2008-07-11
I have 2 HDDs. The 1st one has no OS and the 2nd one has three OS. Ubuntu 8.04 (1st partition), Windows Vista (2nd partition) and Windows XP (3rd partition). I use GRUB. Although the OS are on the 2nd HDD, GRUB is installed in the 1st HDD. I have no problems. It works perfectly and I can still use the LiveCD.

---


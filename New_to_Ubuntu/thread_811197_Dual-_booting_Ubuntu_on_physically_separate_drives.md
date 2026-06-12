---
title: "Dual- booting Ubuntu on physically separate drives"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by CompSciSTL on 2008-05-28
Hello,

I'm new to the world of Ubuntu, and after doing some looking over of a few live CDs, I want to install Ubuntu 7.10 (64-Bit) on my Desktop on a drive that is physically separate from my XP Pro drive.  Would a program like Grub (I think) allow me to boot up to a default Hard drive after a short amount of time has passed without pressing a certain button?  

Many thanks in advance!

---

### Post by iaculallad on 2008-05-28
> **CompSciSTL said:**
> Hello,

I'm new to the world of Ubuntu, and after doing some looking over of a few live CDs, I want to install Ubuntu 7.10 (64-Bit) on my Desktop on a drive that is physically separate from my XP Pro drive.  Would a program like Grub (I think) allow me to boot up to a default Hard drive after a short amount of time has passed without pressing a certain button?  

Many thanks in advance!

Yes you could install your Gutsy 64-bit on a separate drive with a 64-bit architecture CPU of course. Ubuntu would automatically configure the GRUB menu for you after installation (it will include your windoze OS). Grub will give you a 3-second (but of course you could change this on /boot/grub/menu.lst file) "think-time" for you to choose what OS you want to load.

---

### Post by CompSciSTL on 2008-06-15
I guess it's possible to install GRUB just on the SATA drive that I want to use for Ubuntu and leave the SATA drive that has Windows XP alone?

---

### Post by CompSciSTL on 2008-06-21
I guess it's possible to put GRUB on the Ubuntu drive only and not mess with the XP drive at all?

I'm sorry for asking, but information about Dual-booting seems a bit scattered about with no definite solution.

---

### Post by macaholic on 2008-06-22
GRUB shouldn't mess with your xp partition, it should jsut recognize it and possibly, if you have it set up correctly, boot it.

---

### Post by CompSciSTL on 2008-06-22
I guess GRUB has been known to install in the windows drive if not properly selected?

Would adjusting the BIOS so the soon to be Ubuntu drive will be ahead of the Windows drive in the boot order help ensure the correct installation of GRUB?

---


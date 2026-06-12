---
title: "Ubuntu Dual Install? (I Think)"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by dj_spooky_07 on 2008-11-12
hello, I'm sorry if this has been answered earlier but I am fairly new with Ubuntu. I have a question regarding installation of the OS. I understand that I can run it off of the same hard drive that I am currently using windows on, but I am curios to see if there is any way that, since i have 2 hard drives in my computer, one master the other slave, can I install Ubuntu on the slave drive and choose whether to start in windows or Ubuntu, or should I do somethingg else? Please help, I am really new at this, as this is my first time working with linux based software.

All help will be greatly appreciated.

---

### Post by steve-shinn on 2008-11-12
Yes you can install Ubuntu on another hard drive :-

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by handydan918 on 2008-11-12
+1
Ubu on a second HD is no problem. Just don't get gun-shy when the installer asks here to put GRUB-put it on the MBR of the 1st disk. You'll just be borrowing trouble otherwise.

---

### Post by Bartender on 2008-11-12
The Ubuntu bootloader (called GRUB) can handle two separate HDD's just as easily as it does one.  If you let Ubuntu auto-install to the second drive GRUB will still place Stage 1 on the first drive's MBR, just like it would with one HDD, and the end result is just as straightforward.
There's one thing you need to be aware of.  The Ubuntu installer will recognize your drives as sda and sdb.  Make sure to install Ubuntu to sdb, not sda!  This will be pretty clear as you're going thru the installation steps.
Wait, there are two things to be aware of.  You can if you wish install the entire Ubuntu installation to the second HDD.  GRUB Stage 1 and all.  The Windows HDD is entirely unaffected.  Then you choose which device to boot by tapping a key while the PC is first booting up (which key that is depends on your BIOS).  This method isn't *harder* than the usual method, but you have to know a bit more about GRUB and know how to tell the Ubuntu installer to put EVERYTHING on the second drive.

---

### Post by caljohnsmith on 2008-11-12
> **Bartender said:**
> 
Wait, there are two things to be aware of.  You can if you wish install the entire Ubuntu installation to the second HDD.  GRUB Stage 1 and all.  The Windows HDD is entirely unaffected.  Then you choose which device to boot by tapping a key while the PC is first booting up (which key that is depends on your BIOS).  This method isn't *harder* than the usual method, but you have to know a bit more about GRUB and know how to tell the Ubuntu installer to put EVERYTHING on the second drive.
+1. If you click the "advanced" button in the final stage of the Ubuntu installation process, you can specify where to install Grub to; by default it will be installed to (hd0), also known as /dev/sda, and that's your Windows drive. That way you can simply reboot after the installer is done and get a Grub menu on start up; but as Bartender points out, now your drives are dependent on each other, so if anything happens to either of them, you most likely won't be able to boot at all. 

It is more ideal to use the advanced button and have Grub installed to /dev/sdb (or whichever is your external drive), and then simply change your BIOS so that the external drive boots first on start up. That way if anything happens to the external HDD, your Windows HDD is untouched and should boot fine. If you need any more specifics, let us know. :)

---

### Post by Duck2006 on 2008-11-12
> **handydan918 said:**
> +1
ubu on a second hd is no problem. Just don't get gun-shy when the installer asks here to put grub-put it on the mbr of the 1st disk. You'll just be borrowing trouble otherwise.

+2

---


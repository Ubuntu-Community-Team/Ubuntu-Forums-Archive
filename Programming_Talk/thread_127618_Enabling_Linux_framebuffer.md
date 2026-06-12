---
title: "Enabling Linux framebuffer"
date: 2006-02-09
forum: Programming Talk
---

### Post by rup on 2006-02-09
How do I enable the Linux framebuffer device? 

I followed the steps at this site: 
[http://doc.trolltech.com/qtopia1.6/html/HOWTO-framebuffer.html](http://doc.trolltech.com/qtopia1.6/html/HOWTO-framebuffer.html)
and ended up creating a customised kernel. But I'm unable to boot this kernel.Below are the last few lines that appear while booting and then, nothing happens.
-------------------------------------------------------------------------
.
.
Uncompressing Linux... OK, booting kernel
.
.
[4294667.296000]BIOS provided physical RAM map:
[4294667.296000]0MB HIGHMEM available
[4294667.296000]223MB LOWMEM available
[4294667.296000]found SMP MP-table at 00ff780
[4294667.296000]DMI 2.3 present
--------------------------------------------------------------------------

I edited menu.lst in /boot/grub to boot this kernel. Is that causing problems? But I couldn't find grub.conf in Ubuntu. 
(in fact in RedHat, I had to edit grub.conf to enable the framebuffer device)

---

### Post by jerome bettis on 2006-02-09
you have to append vga=0x123 to the end of the kernel line in grub.  123 are different for every monitor, my laptop uses 0x0317.  there's also two different drivers that take different arguments there.

maybe this will help, [http://www.ubuntuforums.org/showthread.php?t=124036&highlight=framebuffer](http://www.ubuntuforums.org/showthread.php?t=124036&highlight=framebuffer)

---

### Post by rup on 2006-02-10
Thank you, Framebuffer is working now!

---


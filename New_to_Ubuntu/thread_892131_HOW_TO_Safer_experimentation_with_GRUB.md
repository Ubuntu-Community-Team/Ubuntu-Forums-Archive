---
title: "HOW TO: Safer experimentation with GRUB"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by rated727 on 2008-08-16
after a few unsuccessful experiments with GRUB I now offer the following:

If you ever experiment with GRUB and found that you have created a monster, (boot failure) you have a problem.

For me, the solution has been to start in "recovery mode" - drop to the shell (command interface) - restore the previous working copy of /boot/grub/menu.lst (now with some other name) to menu.lst - then reboot.

But, what if ...

I copied the entire load subsection and inserted it immediately below itself. (see below)  and modified the second copy - now called (experimental)

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9d9eec16-baf5-4774-ace7-be6b69a65e3c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (experimental)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9d9eec16-baf5-4774-ace7-be6b69a65e3c ro verbose vga=0x0129
initrd		/boot/initrd.img-2.6.24-19-generic
verbose

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
(blah - blah - blah)

The modifications that I made above turn off the splash-screen/progress-meter and instead "verbose" shows all the text stuff that the splash is supposed to hide ... and VGA= sets up the text display to 132 columns (normally 80) to reduce line wrap.  "verbose" on the last line turns off the shutdown splash-screen/progress-meter


If the "experimental" boot fails or otherwise doesn't do what I want, I only have reboot to load from the unaltered first <default> GRUB menu item.  Then I can edit the "experimental" section after a normal start ... much easier than any other method that I've tried.

---


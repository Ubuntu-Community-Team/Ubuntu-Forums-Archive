---
title: "quick question on how to adjust GRUB"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by dnns123 on 2008-06-07
The new updates made my GRUB boot list a lot longer. with Linux kernel .16 to .18
How do I deleted the .16 and .17 from the list? just delete the lines from the menu.lst?

> 
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


into

> 
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


---

### Post by TeoBigusGeekus on 2008-06-07
If I were you, I would uninstall the -16 kernel with Synaptic and just comment out (add # in front of them) the -17 entries in grub. If something goes wrong with the -18 kernel, you can always switch to the older version and have your system up and running...

---

### Post by sisco311 on 2008-06-07
Just comment out the unneeded entries:
> title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

#title		Ubuntu 8.04, kernel 2.6.24-17-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-17-generic #root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-17-generic
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-17-generic #root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro single
#initrd		/boot/initrd.img-2.6.24-17-generic

#title		Ubuntu 8.04, kernel 2.6.24-16-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-16-generic #root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-16-generic #root=UUID=f8cd4659-3415-49a4-aaf5-936b0bd6f291 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1 			 		


---

### Post by dnns123 on 2008-06-07
you can uninstall the kernel with synaptic? didnt know that...
ill think about your suggestion

---

### Post by meierfra. on 2008-06-07
drs305 wrote a HowTo on this subject:

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by kansasnoob on 2008-06-07
I'd use the first option listed in the tutorial posted by 'meierfra'.

Using Startup-Manager is just soooooooooo easy!

---

### Post by dnns123 on 2008-06-07
i dont like start-up manager... i was traumatized by it months ago... i do most things manually now.

---


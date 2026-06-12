---
title: "How do I add Mac OS X86 10.5 (external hdd) to the grub boot list?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by abh83 on 2008-05-31
How do I add Mac OS X86 10.5 to the grub boot list?

I just installed Mac OS X86 on my external SATA USB hardrive.

I have an internal SATA harddrive on which windows xp and ubuntu 8.04 is installed.

this is a cut out of my current menu.lst:

```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a4d25da8-08cf-40a7-8b93-18c23d97973a ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a4d25da8-08cf-40a7-8b93-18c23d97973a ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a4d25da8-08cf-40a7-8b93-18c23d97973a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a4d25da8-08cf-40a7-8b93-18c23d97973a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by abh83 on 2008-06-01
anyone? :(

---

### Post by abh83 on 2008-06-01
i guess something like this:

title Mac OS X
root(hdx,x) x depends on your system
makeactive
chainloader +1

however, how do  i find the root of my external usb hdd?

---

### Post by bumanie on 2008-06-01
I'm not too sure, that's why I haven't answered. I suspect that if you make it bootable as far as giving it a boot flag, grub will look for it each time you boot up and if it's not plugged in grub will give an error. If you are trying to have macosx as a bootable OS off an external drive, I think you will run into problems. Someone else may know more than I, but I know people who've tried the same with ubuntu (unless following a guide to make external linux devices bootable), always run into grub issues. Basically what you have put on your sample grub list would be correct, but I think you will end up with booting issues unless that external drive is always plugged in. I can't guarantee that I'm right, but that's the best 'educated' (or uneducated) guess I can make. I know nothing about mac's bootloader.

---

### Post by abh83 on 2008-06-01
Thank you for your time but I managed to solve the problem.

Usually I should be able to automatically boot from my external usb drive when its plugged in... which was not the case by me. It turns out something was wrong with the partitions! :)

---


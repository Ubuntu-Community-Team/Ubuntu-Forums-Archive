---
title: "Kernel panic"
date: 2005-03-06
forum: Packaging and Compiling Programs
---

### Post by GLDavid on 2005-03-06
Hello

I have Ubuntu x86 for my AMD64. I have downloaded the kernel 2.6.11 from kernel,org and I want to compile it. No problem during the compilation but when I reboot my computer, I have this kernel panic error :
```
kernel panic : not syncing; VFS; Unable to mount root fs on unknown-bloc (0,0)
```
 :-( 
Very bad !
Here's my menu.lst from grub :
```
title      Windows XP
root      (hd0,0)
makeactive
chainloader   +1

title      Ubuntu, kernel 2.6.11.050305
root      (hd0,5)
kernel      /boot/vmlinuz-2.6.11.050305 root=/dev/hda6 ro quiet splash
initrd      /boot/initrd.img-2.6.11.050305
savedefault
boot

title      Ubuntu, kernel 2.6.11.050305 (recovery mode)
root      (hd0,5)
kernel      /boot/vmlinuz-2.6.11.050305 root=/dev/hda6 ro single
initrd      /boot/initrd.img-2.6.11.050305
savedefault
boot

title      Ubuntu, kernel 2.6.8.1-5-386
root      (hd0,5)
kernel      /boot/vmlinuz-2.6.8.1-5-386 root=/dev/hda6 ro quiet splash
initrd      /boot/initrd.img-2.6.8.1-5-386
savedefault
boot

title      Ubuntu, kernel 2.6.8.1-5-386 (recovery mode)
root      (hd0,5)
kernel      /boot/vmlinuz-2.6.8.1-5-386 root=/dev/hda6 ro single
initrd      /boot/initrd.img-2.6.8.1-5-386
savedefault
boot

title      Memory test
root      (hd0,5)
kernel      /boot/memtest86+.bin
```

I have the kernel panic error even if I compile with the Debian method (make-kpkg) with or without the initrd option.
Thanks for your answers.

Bye bye.

---

### Post by Kimm on 2005-03-10
> 
I have Ubuntu x86 for my AMD64


does that even work?? Perhaps the new amd64 kernel doesnt like all the x36 software??

---

### Post by Antto on 2005-03-11
Hi. I just registered to this forum for this question. I used linux the first time about 4 days ago and i wanted to have dvb support so I compiled the new kernel, which was, let just say it wasn't very easy for a complete linux newbie but i got that same message so many times it still haunts my dreams =), Well anyway after a LOT of recompiles i was led to the fact i hadn't installed all the required IDE and SATA drivers in the kernel, so i  suggest you go trough the config and try to enable the right ide drivers to boot your system. Hope this helps

---


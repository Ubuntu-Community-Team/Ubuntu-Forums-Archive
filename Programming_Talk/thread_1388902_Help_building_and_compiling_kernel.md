---
title: "Help building and compiling kernel"
date: 2010-01-23
forum: Programming Talk
---

### Post by swappo1 on 2010-01-23
Hello,

I am trying to build and compile a kernel to learn to program device drivers.  When I reboot and try to load the new kernel, I get the following:
```

root(hd0,0)
   Filesystem type is ext2fs, patition type 0x83
Kernel /boot/vmlinuz-2.6.32.3 root=/dev/sda1 ro quiet
   [Linuz-bzImage, setup = 0x3000, size = 0xc2040]
initrd /boot/initrd.img-2.6.32.3

Error 15: File Not Found

```

I don't have initrd.img-2.6.32.3 in /boot.  
```
hopchewer@hopchewer:/boot$ ls
config-2.6.26-2-amd64  initrd.img-2.6.26-2-amd64      System.map-2.6.32.3
config-2.6.32.3        initrd.img-2.6.26-2-amd64.bak  vmlinuz-2.6.26-2-amd64
grub                   System.map-2.6.26-2-amd64      vmlinuz-2.6.32.3

```
Any idea why this wasn't created?  How can get this file so I can boot the new kernel?

---

### Post by quixote on 2010-01-25
I've only ever installed one kernel (and that was under duress because I desperately needed specific 64-bit support), so I'm not the best person to answer this....

But my first thought was are you sure you maybe didn't have a corrupted file or download?  Also, have you checked to see whether maybe the file is in / rather than /boot?  (I know.  Kind of like asking whether the computer is turned on.  Sorry.)  Anyway, if it was me, I'd just start over with a new download from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/)

---


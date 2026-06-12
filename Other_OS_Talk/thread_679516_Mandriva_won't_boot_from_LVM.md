---
title: "Mandriva won't boot from LVM"
date: 2008-01-27
forum: Other OS Talk
---

### Post by louis_nichols on 2008-01-27
Hi everyone!

I thoght I would give Mandriva 2008 a try and I installed it on my old LVM setup, which I have been using for my main Linux installs for 2 years now.

The thing is: it won't boot. I get a "kernel panic - tried to kill init" error.

From my experience, this happens when it cannot mount the filesystem, but I am not sure.


here is my menu.lst
```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,2)/gfxmenu
default 0

title linux
kernel (hd0,2)/vmlinuz BOOT_IMAGE=linux root=/dev/kubuntu/root  resume=/dev/hdb1 vga=791
initrd (hd0,2)/initrd.img

title linux-nonfb
kernel (hd0,2)/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/kubuntu/root  resume=/dev/hdb1
initrd (hd0,2)/initrd.img

title failsafe
kernel (hd0,2)/vmlinuz BOOT_IMAGE=failsafe root=/dev/kubuntu/root  failsafe
initrd (hd0,2)/initrd.img
```

It is correct, in that my root LV is /dev/kubuntu/root so this puzzles me a lot.

I also tried specifying root as /dev/kubuntu-root and /dev/VolGroup00/LogVol00 but no joy.

Any help would be appreciated.

---


---
title: "Lucid - compiling upstream kernel 2.6.34"
date: 2010-05-01
forum: Packaging and Compiling Programs
---

### Post by Eosie on 2010-05-01
Hi,

I've compiled and installed an upstream kernel on Ubuntu Lucid but it doesn't boot. First the step I've taken:

```
make menuconfig
make -j2
sudo make modules_install
sudo make install
sudo update-initramfs -k 2.6.34-rc2 -u
sudo update-grub
```

This works fine on Karmic but when I try to boot the new kernel on Lucid, it prints a backtrace to the console before the plymouth boot screen shows up and even before fbcon jumps in (i.e. it's printed to the standard low-res non-KMS console). BTW update-initramfs did not complain about missing firmware (radeon). My guess is that initramfs hasn't been updated to include plymouth bits but I haven't found how to do this.

Do you have any idea what I am missing?

---

### Post by Eosie on 2010-05-05
It looks like I am the last one compiling upstream kernel on this system. :mad:

---

### Post by dennis.jarosch on 2010-05-10
Did you have a look at this?

[INDENT][https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")[/INDENT]

I compiled a custom kernel ages ago and it worked.

Or grab and install a vanilla kernel from the mainline builds:

[INDENT][https://wiki.ubuntu.com/KernelTeam/MainlineBuilds]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds")[/INDENT]

Good luck!
Dennis

---

### Post by piratesmack on 2010-06-11
Bump

Does Lucid work with a vanilla kernel?

---

### Post by kell_pt on 2010-06-27
I should point out that this kernel solved all my nvidia heat issues (apparently caused by lack of acpi support). Uses to get 90C on my card, now at 45C.

---


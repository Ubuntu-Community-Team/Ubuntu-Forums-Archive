---
title: "system freezes and crashes"
date: 2023-01-20
forum: New to Ubuntu
---

### Post by martinsolieira7007 on 2023-01-20
I am with old PC running with Ubuntu 20.04.01 , with a P5GC-MX/1333 motherboard and 2 DDR2 667MHz 2Gb combs, I also use a gforce 8600GT 512Mb video card. But out of nowhere the system freezes and crashes, nothing works and the way is to restart by the physical button. What can be happening? I tried to install Mint Cinnamon-64btis and gave the same problem.

---

### Post by TheFu on 2023-01-20
I'm fairly certain that nvidia has dropped support for geforce 8600GT drivers.

When it comes to all system crashes, 
a) check the system log files for errors and warnings
b) if nothing is there, just before the time of the crash, then it is likely a hardware issue that prevents anything from being logged.  That could be the GPU, motherboard or PSU.

To remove the current install from the problem list, boot into a usb flash drive Linux/Ubuntu in the "Try Ubuntu" mode and run that at least until a crash happens or a few days without any crash.  Then I'd expect it is NOT a hardware issue.

---

### Post by vmpx on 2023-01-21
I use the additional parameter "nomodeset" in GRUB menu on Ubuntu 18.04 and 20.04 ("quiet splash *nomodeset*").

---

### Post by MAFoElffen on 2023-01-21
> **TheFu said:**
> I'm fairly certain that nvidia has dropped support for geforce 8600GT drivers.

> **vmpx said:**
> I use the additional parameter "nomodeset" in GRUB menu on Ubuntu 18.04 and 20.04.

It is still supported by package nvidia-340...

---


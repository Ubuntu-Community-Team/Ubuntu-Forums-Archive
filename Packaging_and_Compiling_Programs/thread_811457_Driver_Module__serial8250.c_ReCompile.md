---
title: "Driver Module : serial/8250.c ReCompile"
date: 2008-05-29
forum: Packaging and Compiling Programs
---

### Post by peioazkarate on 2008-05-29
Hi,

I have problems with a custom serial card, PCI&16550A UART. To find the bug I would like modify the serial driver 8250.c, compile alone and unload-load the driver.

Actually, I've a custom configured kernel (Ubuntu 7.10/kernel 2.6.22.9) with the serial driver defined as "M" module instead "Y" integrated into the kernel. 

Well, now I see the driver with "lsmod", I can load-unload with "rmmod" and "insmod". 

The question is, how can I compile the serial driver without compiling whole kernel ?, which makefile or util could I use ?.

Best regards,

Peio Azkarate

---

### Post by kingsley_mun on 2008-06-01
I too am trying to tweak a custom driver and wish to compile only the driver module and not the entire kernel. I found this link but can not confirm that the procedure is working as of yet. [Link]("http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html")

Please post if you have made any progress. Thanks

---


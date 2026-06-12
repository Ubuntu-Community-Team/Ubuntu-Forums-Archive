---
title: "Linux question"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by will1982 on 2012-10-25
I downloaded the linux kernel 3.6.3 as a tar.bz and extracted it. Is there a way I can use it (as in booting the actual Linux kernel)

---

### Post by sandyd on 2012-10-25
> **will1982 said:**
> I downloaded the linux kernel 3.6.3 as a tar.bz and extracted it. Is there a way I can use it (as in booting the actual Linux kernel)

You have downloaded the linux kernel, but im pretty sure its not the linux kernel you are thinking about ;)

The package that you have is the uncompiled source code for the linux kernel, and will have to be configured and compiled before it can be used.

For more info, see [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

btw, just as a hint, the default Ubuntu kernel config options are in /boot/config* , according to your kernel and version.


For newer (precompiled) kernels for Ubuntu, please see [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and download/install linux-image* , linux-headers*, and linux-image-extra* , according to your architecture.

---

### Post by will1982 on 2012-10-25
> **sandyd said:**
> You have downloaded the linux kernel, but im pretty sure its not the linux kernel you are thinking about ;)

The package that you have is the uncompiled source code for the linux kernel, and will have to be configured and compiled before it can be used.

For more info, see [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

btw, just as a hint, the default Ubuntu kernel config options are in /boot/config* , according to your kernel and version.


For newer (precompiled) kernels for Ubuntu, please see [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and download/install linux-image* , linux-headers*, and linux-image-extra* , according to your architecture.

Ah, thanks :P

---


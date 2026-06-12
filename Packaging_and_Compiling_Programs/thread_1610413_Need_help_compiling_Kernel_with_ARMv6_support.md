---
title: "Need help compiling Kernel with ARMv6 support"
date: 2010-10-31
forum: Packaging and Compiling Programs
---

### Post by mrinehart93 on 2010-10-31
Well, I've tried this before in Arch Linux, but I simply got confused beyond belief and am now trying this in Ubuntu. So basically I am attempting to port Palm WebOS over the HTC Hero phone. Now to do this, the kernel must be ported. In order to port the kernel, I need to set up the GNU ARM Toolchain. This is probably the hardest thing I've ever tried to do, no kidding.

So I can get all the binaries installed correctly, but when I am running "make dep" on the Kernel source, it is always missing something, like arm-none-linux-gnueabi or stdarg.h. Now it's simply not realistic so add every single thing that "make dep" needs into my $PATH. Can anyone, preferably someone experienced with compiling kernels, help me out here? This is the one major delay we're having in the project so far, so I need this solved ASAP.

---


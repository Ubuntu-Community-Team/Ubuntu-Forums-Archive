---
title: "cross compiling amd64 packages on i386 system - replacing the kernel"
date: 2006-08-24
forum: Programming Talk
---

### Post by sander marechal on 2006-08-24
Hello,

I am running an AMD64 PC with 32-bit Ubuntu installed (I want things like flash et. al). I am trying to create amd64 deb's with pbuilder. I've read that it is possible to do, but I need to replace my 32-bit kernel with the amd64 one so pbuilder can boostrap and amd64 system.

So, I downloaded the linux-image and linux-restriucted-modules amd64 packages and tried to install them with dpkg -i --force-architecture. The kernel works, but not the restricted modules. I get this:

```
sander@tweety:~/kernels$ sudo dpkg -i --force-architecture linux-restricted-modules-2.6.15-26-amd64-k8_2.6.15.11-3_amd64.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (amd64) does not match system (i386)
(Reading database ... 93680 files and directories currently installed.)
Preparing to replace linux-restricted-modules-2.6.15-26-amd64-k8 2.6.15.11-3 (using linux-restricted-modules-2.6.15-26-amd64-k8_2.6.15.11-3_amd64.deb) ...
Unpacking replacement linux-restricted-modules-2.6.15-26-amd64-k8 ...
Setting up linux-restricted-modules-2.6.15-26-amd64-k8 (2.6.15.11-3) ...
ath_hal/ah_osdep.o: file not recognized: File format not recognized
fcdsl2/devif.o: file not recognized: File format not recognized
fcdslsl/devif.o: file not recognized: File format not recognized
fcdslslusb/buffers.o: file not recognized: File format not recognized
fcdslusb/buffers.o: file not recognized: File format not recognized
fcdslusb2/buffers.o: file not recognized: File format not recognized
fcpci/driver.o: file not recognized: File format not recognized
fcpcmcia/driver.o: file not recognized: File format not recognized
fcpcmcia_cs/fcpcmcia_cs.mod.o: file not recognized: File format not recognized
fglrx/fglrx.mod.o: file not recognized: File format not recognized
new_ath_hal/ah_osdep.o: file not recognized: File format not recognized
nvidia/nv-i2c.o: file not recognized: File format not recognized
nvidia_legacy/nvidia.mod.o: file not recognized: File format not recognized

```

I can boot the system fine with the kernel only, but I need to start plain X manually because I use nvidia-glx and XGL so X crashes on boot. I can start X manually after that with the startx command after logging in.

So, can I replace my 32 bit kernel with a 64 bit kernel and still have nvidia-glx / XGL? How can I get the restricted-modules amd64 package properly installed?

---


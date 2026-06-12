---
title: "Compiling kernel from source"
date: 2010-11-19
forum: Packaging and Compiling Programs
---

### Post by jcwx86 on 2010-11-19
Hi,

I have recently been attempting to compile a kernel (2.6.32-25) for my netbook (Eee PC 701SD, i386, Ubuntu 10.04). I needed to compile a custom kernel to test a patch for my wireless driver.

I used this document,
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
obtaining the source using apt-get and successfully patching the kernel using
```
patch -p1 < patch
```
in the source directory.

I then compiled the (generic-pae flavour) kernel successfully using various commands with
```
debian/rules
```

I had little problem compiling the kernel, however, I have a few questions I'd like to ask.

1) I could see no way to carry over the configuration from my netbook's current kernel (another generic-pae flavour kernel) to the one I was compiling. Is it necessary to change the configuration files for a kernel before compiling if you just want to run a standard desktop system?

2) Is there any way to append something to the end of the kernel name using this method? I'd like to add "-custom" so that I can differentiate it from mainstream kernels installed on my system. Installing the kernel on my netbook meant overwriting the current mainstream 2.6.32-25-generic-pae kernel.

I'm coming at this from the point of view of someone who has more experience compiling kernels using the "old fashioned" Debian method, i.e. 
[https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way)

I decided to compile a kernel using this method as I knew how to append something to the end of the kernel. However, this did not give me the option of which flavour of kernel I wanted to compile.

3) What do the different "flavours" add to the kernel?

In addition, I didn't seem to be able to use the configuration from my netbook's mainstream 2.6.32-25-generic-pae kernel to use as a basis for the custom kernel as when I compiled a kernel using this method with the config file it caused my netbook to be unable to boot from that GRUB menu selection. I compiled the kernel using the default configuration.

4) Is there any harm in compiling a kernel using the default configuration (i.e. that obtained by not changing any of the settings in make menuconfig)?

I am currently using the custom kernel compiled the "old fashioned" Debian way and it seems to be working fine (the patched driver works, too), but I am wondering if by using this kernel I am affecting the performance of functionality of my OS in ways I don't yet know.

I'd be grateful for any answers to these questions. Thanks!

---


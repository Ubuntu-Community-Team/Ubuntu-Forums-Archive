---
title: "Package cross compiling"
date: 2015-07-15
forum: Packaging and Compiling Programs
---

### Post by Silvan_Murer on 2015-07-15
Hello all,
I develop a new, own Ubuntu package. The development environment is an Ubuntu 64bit (14.04 LTS).
I will develop the package for 32bit and 64 bit. Right now I have a small problem by developing the 32bit package.
The package include a shared library which should compiled with the –fPIC option. I can build the library for both (64 and 32bit[wit –m32] ) but when I check the debian package with “lintian” I become an error in the 32bit version: shlib-with-non-pic-code
What can I do, to compile the 32bit application with PIC? (I add the –fPIC compiler option…)
Thanks for your support
Best regards,
Silvan

---

### Post by Silvan_Murer on 2015-07-17
Ok,
I found the failure. The problem was in a external library (libusb). The installation of both (32 and 64bit version) from libusb failed. The result was only that the finale 32bit library didn't support the PIC... 
By fixing the wrong libusb installatio with a manual placement from this library files, the problem was solved and the build environment works...

---


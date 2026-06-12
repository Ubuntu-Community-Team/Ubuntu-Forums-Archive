---
title: "Unable to run program on Ubuntu 64bits: libgsl problems"
date: 2012-09-20
forum: Programming Talk
---

### Post by cosmo1key on 2012-09-20
Dear all,
My machine is i7-3770 and with Ubuntu 12.04 64bits. I have encountered a problem when I tried to run a program via mpirun (more precisely it's a openly shared program called GADGET-2 for cosmological simulations). It's a public code that I do not write myself. When I entered a command line the message
"error while loading shared libraries: libgsl.so.0: wrong ELF class: ELFCLASS64"
appears. 

When I searched for a solution it seems the problem comes from the version of Ubuntu that the library does not support 64 bit version. 

By the way normal programming as when I complied my own C programs does not have this kind of problem. And previously I was working with 32bits and I had no problem like this.

Could we fix it? Or should I change back to Ubuntu 32bits (as I worked with for a while). Or should I install a virtual machine running on 32bits?

Comments and suggests are welcome.
Many thanks in advance

cosmo1key

---

### Post by pqwoerituytrueiwoq on 2012-09-20
```
sudo apt-get install ia32-libs
```
then you can run 32bit executable files

---

### Post by cosmo1key on 2012-09-20
To pqwoerituytrueiwoq

I install the package you mentioned but the same problem persists. But anyway thank you for suggestion. Is it possible that the code itself supports only 32 bit version of gsl?


cosmo1key

---

### Post by einonm on 2012-09-20
the 32 bit version of libgsl is not included in the ia32-libs package. 

There does seem to be a 32bit i386 package available:

sudo apt-get install libgsl0ldbl:i386 

If that doesn't work, you could try searching for how to install 32bit libraries on ubuntu 64bit, there seems to be a few methods available (including using chroot to 32bit).

---

### Post by cosmo1key on 2012-09-22
> **einonm said:**
> the 32 bit version of libgsl is not included in the ia32-libs package. 

There does seem to be a 32bit i386 package available:

sudo apt-get install libgsl0ldbl:i386 

If that doesn't work, you could try searching for how to install 32bit libraries on ubuntu 64bit, there seems to be a few methods available (including using chroot to 32bit).


Billions of thanks!!! This fixed my problem. 

cosmo1key

---


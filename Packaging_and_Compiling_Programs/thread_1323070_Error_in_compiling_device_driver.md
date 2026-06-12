---
title: "Error in compiling device driver"
date: 2009-11-11
forum: Packaging and Compiling Programs
---

### Post by rohitkugve on 2009-11-11
Hi all,

I am trying to compile the device driver for Moxa RS485 PCI card( [http://www.moxa.com/product/CP-132.htm](http://www.moxa.com/product/CP-132.htm) ). The instruction is to compile the drive by using make. When I do make I get the following error 

[B]/home/rohit/Downloads/mxser/driver/mxser.c: In function ‘mxser_flush_buffer’:
/home/rohit/Downloads/mxser/driver/mxser.c:1990: error: request for member ‘ops’ in something not a structure or union
make[3]: *** [/home/rohit/Downloads/mxser/driver/mxser.o] Error 1
make[2]: *** [_module_/home/rohit/Downloads/mxser/driver] Error 2
[/B]

I am using Ubuntu-9.10 with kernel-2.6.31-14-generic. The kernel headers are installed in /usr/src. I have not downloaded the kernel source as I read that its not necessary. I am new to compiling drivers, any idea how to resolve this?

Thanks in advance,
-Rohit

---

### Post by SevenMachines on 2009-11-11
seems to be a pointer thing. it compiles on 2.6.32 if you change 
tty->ldisc.ops
to
tty->ldisc->ops
in driver/mxser.c and driver/mxupcie.c
see attached diff, obviously i can only say that it compiles, not that it works! as the build.log says, kernels greater than 2.6.28 are unsupported

---

### Post by SevenMachines on 2009-11-11
using driv_linux_smart_v1.14_build_09061611.tgz, hope thats the same one you meant

---

### Post by rohitkugve on 2009-11-11
> **SevenMachines said:**
> using driv_linux_smart_v1.14_build_09061611.tgz, hope thats the same one you meant
Yes this is the driver that I ment. I changed the "." to "->" as u said and it is compiling. Have to check if it works today. Curiously, the dame driver code compiles without fuss in Fedora Core 11, running kernel-2.6.30! Thanks a lot.

---

### Post by rohitkugve on 2009-11-12
The driver is working fine with the hardware.
Thank you SevenMachines.

---

### Post by mmb.prog on 2010-05-12
thanks alot :popcorn:

---


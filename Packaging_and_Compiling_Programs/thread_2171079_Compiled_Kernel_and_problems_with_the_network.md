---
title: "Compiled Kernel and problems with the network"
date: 2013-08-29
forum: Packaging and Compiling Programs
---

### Post by danylo-19 on 2013-08-29
Hello, I hope someone can help me.
In my Operating Systems course let us compile a Linux kernel.
I'm using Ubuntu 12.04 LTS
I compiled 2.6.34.14 Kernel following the next guide
[http://mitchtech.net/compile-linux-kernel-ubuntu-12-04-lts/](http://mitchtech.net/compile-linux-kernel-ubuntu-12-04-lts/)
Apparently everything works, except for the network. 
Ubuntu 12.04 with the compiled kernel (2.6.34.14) doesn't recognise my network card and I don't why.
During the compilation there weren't errors (I didn't see anything that looked like an error).
There are no problems with network with my original installation of Ubuntu 12.04 and Windows 7.

---

### Post by GwL3eNC on 2013-08-29
Hi,

I think you are in the wrong category. I assume that there are some modules not
static included in your kernel. I believe it is now like you have to install new
hardware. That means to find out which card you have, find the drivers or
modules and load them. 

This is only a feeling, i hope it's true.

---


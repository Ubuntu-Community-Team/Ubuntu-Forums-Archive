---
title: "cannot compile kernel modules."
date: 2012-08-28
forum: Packaging and Compiling Programs
---

### Post by gmmo1971 on 2012-08-28
Hi,

I am trying to build a hello world kernel module following this article:

[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN40](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN40)

And it uses the makefile below:

obj-m += hello-1.o
all:
   make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
   make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

but when I try to build I always get this:
gustavo@gustavo-Null:~/Desktop/projects/kernel_mod$ make
make -C /lib/modules/3.2.0-29-generic-pae/build M=/home/gustavo/Desktop/projects/kernel_mod modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
scripts/Makefile.build:44: /home/gustavo/Desktop/projects/kernel_mod/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/gustavo/Desktop/projects/kernel_mod/Makefile'.  Stop.
make[1]: *** [_module_/home/gustavo/Desktop/projects/kernel_mod] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [all] Error 2
gustavo@gustavo-Null:~/Desktop/projects/kernel_mod$

I tried lot of different thing but I can't get passed this compilation issue.

Anyone that know about the kernel modules, can explain what should be the verbose of the makefile. It looks like is hiding lots of things and making lots of assumptions. This is making difficult to troubleshoot the problem.

What are the libraries and include paths that should be used? What files am I trying to generate? Is it using gcc to build?

any help is greatly appreciated.

thx.

---

### Post by nativehound on 2012-08-28
The user in that Tutorial is a super user. The ( # ) indicates a super user and The ( $ ) indicates a regular user.

Did you try sudo make

---


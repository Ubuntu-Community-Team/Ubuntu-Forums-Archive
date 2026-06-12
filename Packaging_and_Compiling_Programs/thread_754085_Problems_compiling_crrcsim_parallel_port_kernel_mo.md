---
title: "Problems compiling crrcsim parallel port kernel module"
date: 2008-04-13
forum: Packaging and Compiling Programs
---

### Post by rhauff on 2008-04-13
Hi,
I'm getting a few compile errors then failure, starting with 
 " warning: "CONFIG_MODVERSION" is not defined"

I'm running Xubuntu 7.10 and have not compiled anything on this system before (all installs done by synaptic).  I now installed linux-source for my kernel and build-essential.

I am trying to compile the kernel module for a parallel port RC Simulator interface for crrcsim (model airplane simulator).  This particular module isn't highly supported, but does have a rudimentary makefile for the 2.6 kernel.  I'v copied it here:

KSRC=/lib/modules/2.6.22-14-generic/build

obj-m = rctran2.o

build:
	make -C $(KSRC) SUBDIRS=`pwd` modules

install:
	@# completely broken ATM - removes the whole dir
	@#make -C $(KSRC) SUBDIRS=`pwd` modules_install
	@echo "Install it yourself ..."

clean:
	@# kbuild can't handle this (yet ?)
	@#make -C $(KSRC) SUBDIRS=`pwd` clean
	rm -f *.o *.ko *.mod.o *.mod.c .*.{cmd,flags}
	rm -rf config.status config.log autom4te*.cache


I am compiling with the following command:
make -f Makefile

The following is my list of errors:

make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/roland/Downloads/crrcsim-0.9.8-2/interface_rctran2/kernel_module/rctran2.o
/home/roland/Downloads/crrcsim-0.9.8-2/interface_rctran2/kernel_module/rctran2.c:15:5: warning: "CONFIG_MODVERSION" is not defined
/home/roland/Downloads/crrcsim-0.9.8-2/interface_rctran2/kernel_module/rctran2.c:42: error: expected ‘)’ before string constant
/home/roland/Downloads/crrcsim-0.9.8-2/interface_rctran2/kernel_module/rctran2.c:46: error: expected ‘)’ before string constant
/home/roland/Downloads/crrcsim-0.9.8-2/interface_rctran2/kernel_module/rctran2.c: In function ‘rctran_init’:
/home/roland/Downloads/crrcsim-0.9.8-2/interface_rctran2/kernel_module/rctran2.c:154: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
/home/roland/Downloads/crrcsim-0.9.8-2/interface_rctran2/kernel_module/rctran2.c:154: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/roland/Downloads/crrcsim-0.9.8-2/interface_rctran2/kernel_module/rctran2.o] Error 1
make[1]: *** [_module_/home/roland/Downloads/crrcsim-0.9.8-2/interface_rctran2/kernel_module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [build] Error 2


Any ideas???
Thanks!

---

### Post by my64 on 2008-04-16
The driver is probably outdated with kernel 2.6.
Ask the question on the "crrcsim" list on Yahoo groups, may be someone knows in more details.
Olivier

---


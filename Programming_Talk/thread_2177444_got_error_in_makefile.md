---
title: "got error in makefile"
date: 2013-09-28
forum: Programming Talk
---

### Post by Rahul04789 on 2013-09-28
Following is my makefile:

obj-m:=.pendriver.o

KDIR=/lib/modules/$(shell uname -r)/build
PWD = $(shell pwd)
all:
        make -C $(KDIR) SUBDIRS=$(PWD) modules
clean:
        rm -rf *.o *.ko *.mod.* *.symvers 


I am getting the following error:

rahul@rahul-VPCEG28FN:~/modules/devicedriver/pendrive$ make
make -C /lib/modules/3.5.0-39-generic/build SUBDIRS=/home/rahul/modules/devicedriver/pendrive modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-39-generic'
make[2]: *** No rule to make target `/home/rahul/modules/devicedriver/pendrive/.pendriver.c', needed by `/home/rahul/modules/devicedriver/pendrive/.pendriver.o'.  Stop.
make[1]: *** [_module_/home/rahul/modules/devicedriver/pendrive] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-39-generic'
make: *** [all] Error 2


Tell me what should I do??

Thanks

---

### Post by spjackson on 2013-09-28
> **Rahul04789 said:**
> 
obj-m:=.pendriver.o

Tell me what should I do??


Remove the dot before pendriver perhaps?

---


---
title: "Unable to compile kernel modules"
date: 2011-09-10
forum: Programming Talk
---

### Post by pawan_dear on 2011-09-10
**i am getting this error**

make -C /lib/modules/ 2.6.32-71.el6.x86_64/build M=/home/kk modules
make[1]: Entering directory `/lib/modules'
make[1]: Warning: File `2.6.32-71.el6.x86_64/build' has modification time 6.8e+03 s in the future
make[1]: Nothing to be done for `2.6.32-71.el6.x86_64/build'.
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules'
make: *** [modules] Error 2

**my Makefile is:-**

obj-m+=trivial.o

modules:
        make -C /lib/modules/ $(shell uname -r)/build M=$(PWD) modules

modules_install:
        make -C /lib/modules/ $(shell uname -r)/build M=$(PWD) modules_install

modules_clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules_clean


**your help appreciate**

---


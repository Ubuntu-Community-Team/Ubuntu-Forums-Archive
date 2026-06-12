---
title: "Trouble compiling makefile for module"
date: 2014-04-06
forum: Packaging and Compiling Programs
---

### Post by prasanna5 on 2014-04-06
This is the code of my makefile I have been trying to compile:
obj-m += first.0
KDIR = /usr/src/$(shell uname -r)
        
all:
    make -C /lib/modules/$(shell uname -r)/build $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
clean:
    rm -rf *.o *.ko *.mod *.symvers *.order 

In return I am getting this error:
make -C /lib/modules/3.8.0-29-generic/build make -C /usr/src/3.8.0-29-generic SUBDIRS=/home/nageshgb modules
make: *** /usr/src/3.8.0-29-generic: No such file or directory.  Stop.
make: *** [all] Error 2
root@nageshgb-Inspiron-1525:/home/nageshgb# ^C
root@nageshgb-Inspiron-1525:/home/nageshgb# 

Please help. I have tried finding solution to this but could not. makefile

---

### Post by steeldriver on 2014-04-06
It looks like you have not installed the kernel headers for your current kernel

```
sudo apt-get install linux-headers-generic
```

---

### Post by prasanna5 on 2014-04-07
I installed the kernel headers but I get the same error message. Do you think there is something wrong with the code? Or perhaps any other fault? Please help.

---


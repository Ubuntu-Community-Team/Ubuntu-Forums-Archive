---
title: "Unable to build the kernel module"
date: 2015-05-19
forum: New to Ubuntu
---

### Post by murali7 on 2015-05-19
Hi,
I am trying to build my first kernel module in ubuntu and unable to compile due to below erros.

make -C /lib/modules/3.13.0-52-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-52-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-52-generic'
make: *** [all] Error 2

Following is my Make file details:

[B]obj-m = module1.o 
KERNEL = $(shell uname -r)
all: 
    make -C /lib/modules/$(KERNEL)/build M=$(PWD) modules
clean: 
    make -C /lib/modules/$(KERNEL)/build M=$(PWD) clean
[/B]

Can anybody help me out to resolve them.

** Note:** I have downloaded kernel source code and its version is 3.13.0-52.

---

### Post by SeijiSensei on 2015-05-19
Did you install the **build-essential** package?  If you want to compile kernel modules, you'll need the **dkms** package as well.

---

### Post by murali7 on 2015-05-20
Hi,

Yeah, I have installed the above packages as you told but still the same issue is occuring.

---

### Post by SeijiSensei on 2015-05-20
Well the obvious error is this:
```
/usr/src/linux-headers-3.13.0-52-generic
No such file or directory
```
Is there such a directory? Is that where you put the source?  What kernel are you running on the machine now? (Use "uname -r" to see if you don't know.)  Where did you get the source code? From [https://www.kernel.org/?](https://www.kernel.org/?) 

It's been a *very* long time since I built a kernel from source, so I'm out of ideas.  If you're not using the standard kernel source, I suggest you try that.

---

### Post by tgalati4 on 2015-05-20
There is typically a *.configure* script that is used to check your build environment and flag common errors before *make* is issued.  Do you have a *.configure* script for the module that you are trying to build?  If you don't have one, then search for one from another module that is similar in function to what you are trying to build.

---


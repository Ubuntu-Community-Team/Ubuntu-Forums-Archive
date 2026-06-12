---
title: "Problems compiling truecrypt from source"
date: 2008-01-24
forum: Packaging and Compiling Programs
---

### Post by protokol on 2008-01-24
I've followed the various guides i've found online, and i still get an error when i try to compile it. the error:

```
theeric@ubuntu:/usr/src/truecrypt-4.3a-source-code/Linux$ sudo ./build.sh 
Checking build requirements...
Building kernel module... make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make: *** [truecrypt] Error 2
Error: Failed to build kernel module

```

does anyone have any tips?

---

### Post by Gannin on 2008-01-24
Do you have the kernel header files installed?

---

### Post by protokol on 2008-01-24
yes, i have installed:

linux-headers-2.6.22-14
linux-headers-2.6.22-14-generic
linux-headers-2.6.22-14-server
linux-headers-generic

---


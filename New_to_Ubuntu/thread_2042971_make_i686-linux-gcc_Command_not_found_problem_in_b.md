---
title: "make: i686-linux-gcc: Command not found problem in building kernel"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by arunes007 on 2012-08-15
hiii!!!
i am trying to build a kernel linux-3.6 rc1 bt in buildng the kernel when i ran following command
```

make CROSS_COMPILE = i686 - linux -ARCH = i386

```
i got following error.
/home/abc/Desktop/softwares/linux-3.6-rc1/scripts/gcc-version.sh: line 25: i686-linux-gcc: command not found
/home/abc/Desktop/softwares/linux-3.6-rc1/scripts/gcc-version.sh: line 26: i686-linux-gcc: command not found
make: i686-linux-gcc: Command not found
make[1]: Nothing to be done for `all'.
make[1]: Nothing to be done for `relocs'.
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CC      kernel/bounds.s

any suggestions to get me out of this..

---

### Post by ubudog on 2012-08-15
Try installing the build-essential package:
```
sudo apt-get install build-essential
```

Best,
ubudog

---

### Post by arunes007 on 2012-08-15
> **ubudog said:**
> Try installing the build-essential package:
```
sudo apt-get install build-essential
```Best,
ubudog
build essential is already installed and it is of newest version....

---


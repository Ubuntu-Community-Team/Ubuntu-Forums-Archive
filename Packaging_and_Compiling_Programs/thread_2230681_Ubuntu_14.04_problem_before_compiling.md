---
title: "Ubuntu 14.04 problem before compiling"
date: 2014-06-20
forum: Packaging and Compiling Programs
---

### Post by ManthanRB on 2014-06-20
Hello,

I am trying to compile a kernel for my android device but it throwing errors which used to work properly in my 32bit lubuntu.

```
root@Mario:/home/manthanrb/Android/Source/4.0.2.A.0.84/kernel# make clean && make mrproper
make: /home/manthanrb/Android/Toolchain/arm-eabi-4.4.3/bin/arm-eabi-gcc: Command not found
make[2]: /home/manthanrb/Android/Toolchain/arm-eabi-4.4.3/bin/arm-eabi-gcc: Command not found
/home/manthanrb/Android/Source/4.0.2.A.0.84/kernel/scripts/gcc-version.sh: line 25: /home/manthanrb/Android/Toolchain/arm-eabi-4.4.3/bin/arm-eabi-gcc: No such file or directory
/home/manthanrb/Android/Source/4.0.2.A.0.84/kernel/scripts/gcc-version.sh: line 26: /home/manthanrb/Android/Toolchain/arm-eabi-4.4.3/bin/arm-eabi-gcc: No such file or directory
make: /home/manthanrb/Android/Toolchain/arm-eabi-4.4.3/bin/arm-eabi-gcc: Command not found
make[2]: /home/manthanrb/Android/Toolchain/arm-eabi-4.4.3/bin/arm-eabi-gcc: Command not found
/home/manthanrb/Android/Source/4.0.2.A.0.84/kernel/scripts/gcc-version.sh: line 25: /home/manthanrb/Android/Toolchain/arm-eabi-4.4.3/bin/arm-eabi-gcc: No such file or directory
/home/manthanrb/Android/Source/4.0.2.A.0.84/kernel/scripts/gcc-version.sh: line 26: /home/manthanrb/Android/Toolchain/arm-eabi-4.4.3/bin/arm-eabi-gcc: No such file or directory

```

i searched and found that 32bit libs are needed so i used

```
apt-get install ia32-libs
```

Got this

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0

E: Package 'ia32-libs' has no installation candidate

```

what can be the solution?

Thanks!

---

### Post by ManthanRB on 2014-06-21
up

---


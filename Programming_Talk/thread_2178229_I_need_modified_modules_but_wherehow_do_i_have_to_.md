---
title: "I need modified modules but where/how do i have to build them?"
date: 2013-10-02
forum: Programming Talk
---

### Post by Sidoney on 2013-10-02
Under OpenSuSE i modified some few module source file under /usr/src/linux,
built the modules in /usr/src/linux and installed only these, automated with a 
script and since several years.
Now i want to do the same under Ubuntu with the kernel 3.8.0-31-generic,
with the sources from ubuntu packages, but there is no /usr/src/linux 
and i see confusing directories in /usr/src which may be the right place
to make the modules:

591M  in  ./linux-3.8.0
95M   in  ./linux-headers-3.8.0-31
13M   in  ./linux-headers-3.8.0-31-generic

The source files which i have to modify are in linux-3.8.0, but i have 
version 3.8.0-31-generic, so this directory does not seems to be the right 
one. 
So i checked linux-headers-3.8.0-31-generic, where i found configuration
files like .config, but the source files are missing and therefore the make
commands are failing, e. g. make clean. 
The last directory which may be right is therefore linux-headers-3.8.0-31
but there the source files and the configuration files are both missing.
So i have to do some mixing or patching or something else but what exactly? :confused:

---

### Post by tgalati4 on 2013-10-02
Install the kernel source code and it will create all of the required directories.  The processes is similar to OpenSuse, with some minor modifications.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Sidoney on 2013-10-02
> **tgalati4 said:**
> Install the kernel source code and it will create all of the required directories.  The processes is similar to OpenSuse, with some minor modifications.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Ok, but there ist something missing: With 

apt-get source linux-image-$(uname -r)

i get linux-3.8.0,  linux_3.8.0-31.46.diff.gz,  linux_3.8.0-31.46.dsc  and linux_3.8.0.orig.tar.gz.
So i had to patch:

 zcat linux_3.8.0-31.46.diff.gz | patch -p0 2>&1 | tee patch.out

But what to do at the next kernel version, can i apply the patch to the patched 3.8 sources
or do i have to start again, with unpacking linux_3.8.0.orig.tar.gz ? :confused:

---


---
title: "hello Kernel"
date: 2009-11-24
forum: Packaging and Compiling Programs
---

### Post by tapas_mishra on 2009-11-24
I want to write a simple program that says  Hello Kernel to the kernel and want to link the object file as a module to the kernel what steps should I follow or if Linking such a program in kernel will not be right and may cause problem to boot the system

---

### Post by SevenMachines on 2009-11-24
Rather than display my ignorance here I'll point you in the direction of a[ simple tutorial example]("http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html") that might be helpful :)

$ sudo insmod hello.ko
$ sudo rmmod hello
$ dmesg |tail -n2
[16116.718629] Boom go my kernel!
[16118.290485] Bust go my kernel!

about as advanced as I get with kernel modules :)

---

### Post by SevenMachines on 2009-11-24
just to add, you can add custom modules to dkms which you might want to play around with, for example, continuing on with the hello module example...

* create a directory /usr/src/hello-0.1
* cp hello.c and the makefile from the previous example to this directory.
* add a dkms.conf file too, something like
```
PACKAGE_NAME="hello"
PACKAGE_VERSION="0.1"
BUILT_MODULE_NAME[0]="hello"
DEST_MODULE_LOCATION[0]="/kernel/drivers/hello/"
AUTOINSTALL="yes"
```now you can add it to dkms,
$sudo dkms add -m hello -v 0.1
build and install
$sudo dkms build -m hello -v 0.1
$sudo dkms install -m hello -v 0.1

then your module would be available to,
$modprobe hello

or could be added to /etc/modules to load on boot

obviously its in your hands to be careful of whether its something as trivial and harmless as this example or something that does something more advanced and could cause severe kernel problems

---

### Post by tapas_mishra on 2009-11-24
Thanks a lot to all my problem is solved.

---


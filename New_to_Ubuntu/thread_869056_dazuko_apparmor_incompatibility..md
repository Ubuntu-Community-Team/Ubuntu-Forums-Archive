---
title: "dazuko apparmor incompatibility."
date: 2008-07-24
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-24
Hi! I'm Melvin from India.
I installed AVG for linux workstation recently and compiled dazuko kernel module for real time file scanning in ubuntu 7.10.As root, i gave this code. 
```
./configure 
make
make test
insmod dazuko.ko
make install
```
The error was that the module could not be inserted.
Then, i gave this code:
```
sudo rmmod apparmor
sudo insmod dazuko.ko
```
and the dazuko module works, but the apparmor module can't be reloaded.
How important is apparmor, what does it do and how to get it back working with dazuko?

---

### Post by ice60 on 2008-07-24
all apparmor does is monitor the behaviour of programs to profile them, so if somekind of malware tries to modify something within the program to get itself running the malware will be stopped and logged. so there's no problem running dazuko without apparmor.

to get it working with dazuko i think you have to compile the option in to it when you first install it!

EDIT i found these links that may be the same problem (i know you're not using suse, but suse was the first distro to run apparmor) -
[http://computers-stuff.blogspot.com/2007/05/apparmor-and-dazuko-in-opensuse-102.html](http://computers-stuff.blogspot.com/2007/05/apparmor-and-dazuko-in-opensuse-102.html)

[http://www.dazuko.org/tgen.shtml](http://www.dazuko.org/tgen.shtml)
> 2.2 What are the known issues with SUSE Linux? 

Recent SuSE distributions (SUSE Linux 10, SLES 10, SLED 10) include and use AppArmor by default, which is why other modules cannot access the LSM API. This means that it is not possible to use Dazuko in its default configuration on these systems (because Dazuko by default uses the LSM interface on Linux 2.6 kernels). 

As of version 2.3.0 of Dazuko, you can use syscall hooking as an alternative to LSM for Linux 2.6 systems. If you require AppArmor, then you will need to use the syscall hooking method. This must be specified when configuring Dazuko:

$ ./configure --enable-syscalls --mapfile=/path/to/mapfile 

The mapfile (System.map) is usually located in /boot and has the kernel version as a suffix.

---


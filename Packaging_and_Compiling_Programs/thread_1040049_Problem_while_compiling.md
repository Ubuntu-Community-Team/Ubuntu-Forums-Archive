---
title: "Problem while compiling"
date: 2009-01-15
forum: Packaging and Compiling Programs
---

### Post by dsharmaa on 2009-01-15
Hi, 

When I am using this command line :

CONCURRENCY_LEVEL=1 AUTOBUILD=1 fakeroot debian/rules binary-debs

then I am getting following messages, I am not having any clue why this is happening. 

root@ubuntu-desktop:/usr/src/linux-ubuntu-modules-2.6.22-2.6.22# CONCURRENCY_LEVEL=1 AUTOBUILD=1 fakeroot debian/rules binary-debs
Preparing rtai...
install -d /usr/src/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-rtai
cd ubuntu; find . | cpio -dumpl /usr/src/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-rtai
0 blocks
cat /usr/src/linux-ubuntu-modules-2.6.22-2.6.22/debian/config/i386 > /usr/src/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-rtai/.config
# XXX: generate real config
touch /usr/src/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-rtai/ubuntu-config.h
touch /usr/src/linux-ubuntu-modules-2.6.22-2.6.22/debian/stamps/stamp-prepare-rtai
Building rtai...
make -C /lib/modules/2.6.22-14-rtai/build ARCH=i386 M=/usr/src/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-rtai UBUNTU_FLAVOUR=rtai modules
make: *** /lib/modules/2.6.22-14-rtai/build: No such file or directory.  Stop.
make: *** [/usr/src/linux-ubuntu-modules-2.6.22-2.6.22/debian/stamps/stamp-build-rtai] Error 2
root@ubuntu-desktop:/usr/src/linux-ubuntu-modules-2.6.22-2.6.22# 

Can anybody please guide me through this?

Thanks in advance, 

Cheers, 
DP

---

### Post by dsharmaa on 2009-01-15
when I have used this commands 

root@ubuntu-desktop:/usr/src/linux-ubuntu-modules-2.6.22-2.6.22# ls /lib/modules
2.6.22-14-386  2.6.22-14-generic  2.6.22-14-rt  2.6.22-14-server  2.6.22-14-ume  2.6.22-14-virtual  2.6.22-14-xen
root@ubuntu-desktop:/usr/src/linux-ubuntu-modules-2.6.22-2.6.22# ls /lib/modules/2.6.22-14-rt
build

so thats means that I have file with name 2.6.22-14-rt/build but I need something like 2.6.22-14-rtai/build. 

But I cn't find this file, so how I will change the name of this file. 

I would really appreciate if anyone can help me.

---


---
title: "Can't build a kernel"
date: 2017-07-03
forum: Packaging and Compiling Programs
---

### Post by rw1968 on 2017-07-03
Hi,
I'm trying to build a kernel using instructions from here:
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

I last did any kernel development on 2.6 so I'm expecting some things to have changed.
I can't get source for my kernel (ubuntu studio 16.04)  using apt - so I've used git instead.
apt-get produces the following error:

```
rich@Ginetta:~$ apt-get source linux-image-$(uname -r)
Reading package lists... Done
Picking 'linux-hwe' as source package instead of 'linux-image-4.8.0-58-lowlatency'
E: Unable to find a source package for linux-hwe

```

I can't get build dependencies either:

```
rich@Ginetta:~$ sudo apt-get build-dep linux-image-$(uname -r)
[sudo] password for rich: 
Reading package lists... Done
Picking 'linux-hwe' as source package instead of 'linux-image-4.8.0-58-lowlatency'
E: Unable to find a source package for linux-image-4.8.0-58-lowlatency

```


What have I missed?

---


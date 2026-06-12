---
title: "Linux Kernel Installation"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by Man OS on 2013-01-10
Hi !!

I am facing issues with linux kernel development. Actually I am new comer to linux kernel development and the tutorial guided me to install Linux kernel.

I don't know whether the installation of linux kernel is same like installing an OS or like an software.

what i meant that whether i should install this on separate Virtual machine or i should install it on my system which is already running an ubuntu, so if i install this on my ubuntu system will it cause anykind of issues.

---

### Post by Pjotr123 on 2013-01-10
> **Man OS said:**
>  if i install this on my ubuntu system will it cause anykind of issues.

Yes. That's not a good idea: expect frequent breakage and many unsolvable bugs, when using a kernel that's not a default part of a stable Ubuntu release.

In a sense, the kernel *is* the operating system. The rest is "just" a layer around it. This layer needs to be finely tuned and adjusted to the kernel, otherwise all kinds of things may go horribly wrong.

So I'd definitely use the Virtual Machine.

---

### Post by Man OS on 2013-01-10
so how i should install it on a Virtual machine. Actually i want to write some kernel modules. 

Can you please show me some website or can tell me some steps by which i can install this new linux kernel on Virtual Machine.

---

### Post by steeldriver on 2013-01-10
If you just want to build kernel modules for the currently installed kernel, it should be sufficient to install the appropriate kernel headers package

```
sudo apt-get install linux-headers-$(uname -r)
```plus appropriate build tools of course - at least gcc and make - or the build-essential meta package

See [http://www.tldp.org/LDP/lkmpg/2.6/html/lkmpg.html](http://www.tldp.org/LDP/lkmpg/2.6/html/lkmpg.html) for simple examples you can try out

---

### Post by grahammechanical on 2013-01-10
Have you seen this, by the way?

[http://www.kernel.org/faq/]("http://www.kernel.org/faq/")

My guess on this would be to install Ubuntu into a virtual machine or on a separate partition or even a separate machine and then install the development kernels into it.

Then if things break beyond repair you can just re-install and start again. I do not think it wise to install one of these development kernel on our only Ubuntu OS.

Some of us like to test development branches of Ubuntu. Some put in new Linux kernels as soon as they become available. They do the same with other parts of the distribution. But I think we are all agreed that we try this stuff out on an OS installation we can afford to break.

Regards.

---


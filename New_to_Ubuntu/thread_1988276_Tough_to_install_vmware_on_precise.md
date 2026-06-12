---
title: "Tough to install vmware on precise"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by eshant_engineer on 2012-05-27
Hi,

I found 2 problem which are restricting me to install server:

1)```
Your kernel was built with "gcc" version "4.6.3", while you are trying to use 
"/usr/bin/gcc" version "4.6". This configuration is not recommended and VMware 
Server may crash if you'll continue. Please try to use exactly same compiler as
one used for building your kernel. Do you want to go with compiler
```

I have same version of compiler. I tried after renaming gcc-4.6 to gcc-4.6.3 but no luck. After going with "go with compiler 
"/usr/bin/gcc" version "4.6" anyway?" I face second issue.

2) ```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-3.2.0-24-generic/include/     

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 3.2.0-24-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.

```
while checking uname -a tell me this:```
ebuntu@ebuntu-Inspiron-N5110:~$ uname -a
Linux ebuntu-Inspiron-N5110 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Please help me installing it...

Thank You for your reply.

---

### Post by aktiwers on 2012-05-29
I found that the free VMware is outdated and not developed on anymore. I actually got it to run, but very unstabile and crappy. I would suggest trying Virtualbox instead, if that is a possible solution for you.

---

### Post by Cheesemill on 2012-05-29
VMware Server has not been in development for several years now and support for it ended in June last year.

Instead try either VMware Player or Oracle VirtualBox if you want a free solution, or you can pay for a copy of VMware Workstation.

I would recommend using VirtualBox as installation is much easier than the VMware products and you can add a repository to make sure that it stays up to date. See here for VirtualBox installation instructions:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Dave_in_MD on 2012-05-29
> **Cheesemill said:**
> 

I would recommend using VirtualBox as installation is much easier than the VMware products and you can add a repository to make sure that it stays up to date. See here for VirtualBox installation instructions:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Thanks for the link Cheesemill.  I am still cutting my teeth on the Ubuntu install but I use VirtualBox at work, honeypot and test systems, on MS Win so it is just a matter of time before I will want to use it in Ubuntu as well.  I have an older release of Ubuntu running in a VM that I was using to show the Dir of Education what was available.  We are a non profit so free is important.

---


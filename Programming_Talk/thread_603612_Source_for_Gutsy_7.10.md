---
title: "Source for Gutsy 7.10"
date: 2007-11-05
forum: Programming Talk
---

### Post by sriram.venkataramani on 2007-11-05
Hi,

I'm working on this checkpointing software as part of my school coursework and have an issue running the checkpointing software in Ubuntu 7.10 Gutsy Gibbon. 

Now, I downloaded the source for the 2.6.22 kernel, recompiled the same and the checkpointing software works perfectly fine on 2.6.22 kernel. Now, how can I get hold of the exact same kernel source (2.6.22-14) that is used in Ubuntu? How can I find what modifications Ubuntu has made to the kernel source code?

I've looked in kernel.org and they only have upto 2.6.22-11. I will surely post some of the error messages that I get in the software later (if that will help).

Thanks!

---

### Post by lolindrath on 2007-11-05
The easiest way to get the kernel source is to do:

```
sudo apt-get install linux-source
```

This will put a tar.gz in your /usr/src directory that you can extract, that'll contain the latest kernel code.

--Lolindrath

---

### Post by geirha on 2007-11-05
I suggest you read [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) if you haven't allready.

Regarding the changes done from the vanilla kernel, you can find that info at [http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-14-generic](http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-14-generic)

At the bottom of the page there's a link to the 2.6.22-kernel used, linux-source-2.6.22_2.6.22.orig.tar.gz, and a diff that shows all changes made to that source, linux-source-2.6.22_2.6.22-14.46.diff.gz.

However, you get the same files by simply running 
```
apt-get source linux-image-2.6.22-14-generic 
```

---

### Post by sriram.venkataramani on 2007-11-05
Hi geirha,

I got the source code for 2.6.22-14 and compiled the kernel. But when the machine rebooted with the new kernel, I did a "uname -a" and it got back the kernel version as 2.6.22-9.

I know that when it downloaded the source code, the diff was applied to base source code. What can be the issue?

---

### Post by geirha on 2007-11-07
Surely sounds odd. Can't really think of any reasons for this. Did you follow the guide in the wiki?

---

### Post by sriram.venkataramani on 2007-11-08
Yup. I went back and looked at  /proc/version and /proc/version_signature and both have 2.6.22-14 as the kernel version. So looks like I have the latest source. 

I don't know why uname is not showing the same.

---

### Post by geraldm on 2007-11-12
Perhaps to clarify (or else allow me to confuse like I am confused)
The kernels taken from [www.kernel.org](www.kernel.org) have version numbers that
are all dots, NO "-", although testing/ does use -rc1 suffix.
The "-14" is a debian type of packaging number, meaning that 
this one is 14 in a series of "-14.diff.gz"
The last "dot/digit" in 2.6.22.7 would be concealed within the XX.diff.gz.
The dash numbers DO NOT correspond to the kernel's dot numbers,
methinks.

Gerald

---


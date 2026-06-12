---
title: "How to download kernel source for specific kernel version?"
date: 2011-05-15
forum: Packaging and Compiling Programs
---

### Post by AnotherMuggle on 2011-05-15
Hi All,

I spent a large chunk of yesterday trying to download the kernel source for Maverick's default kernel (2.6.35-22).  The problem I have is that when I try to download it with apt-get I get the following:

```
apt-get source linux-image-2.6.35-22-generic
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Picking 'linux' as source package instead of 'linux-image-2.6.35-22-generic'...
```

apt then goes ahead and downloads the source for a more recent kernel version.  It's driving me nuts!  Can anyone help me out?  Is it possible to obtain the source for a specific kernel with apt?

Thanks,
Tom

---

### Post by gmargo on 2011-05-15
The current version of the 10.10 Maverick kernel is 2.6.35-28.50.  The version you are trying to find is a few revisions out-of-date.  "apt-get source" will always download the latest released version.

If you really want the older kernel info, you can get it from the Ubuntu Git repository.  The tags will allow to you select the exact version you want.
```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-maverick.git
```See for more info:
[https://wiki.ubuntu.com/Kernel](https://wiki.ubuntu.com/Kernel)
[https://wiki.ubuntu.com/Kernel/Dev/KernelGitGuide](https://wiki.ubuntu.com/Kernel/Dev/KernelGitGuide)

Or possibly if this is the original Maverick kernel, you can get the parts from:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.35-22.33.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.35-22.33.diff.gz)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.35-22.33.dsc](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.35-22.33.dsc)
(Don't delete the "linux_2.6.35.orig.tar.gz" file - that file will be the same regardless of what version you're trying to get.)

---

### Post by AnotherMuggle on 2011-05-16
> **gmargo said:**
> The current version of the 10.10 Maverick kernel is 2.6.35-28.50.  The version you are trying to find is a few revisions out-of-date.  "apt-get source" will always download the latest released version.

If you really want the older kernel info, you can get it from the Ubuntu Git repository.  The tags will allow to you select the exact version you want.
```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-maverick.git
```See for more info:
[https://wiki.ubuntu.com/Kernel](https://wiki.ubuntu.com/Kernel)
[https://wiki.ubuntu.com/Kernel/Dev/KernelGitGuide](https://wiki.ubuntu.com/Kernel/Dev/KernelGitGuide)

Or possibly if this is the original Maverick kernel, you can get the parts from:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.35-22.33.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.35-22.33.diff.gz)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.35-22.33.dsc](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.35-22.33.dsc)
(Don't delete the "linux_2.6.35.orig.tar.gz" file - that file will be the same regardless of what version you're trying to get.)

Great, thank you!

---


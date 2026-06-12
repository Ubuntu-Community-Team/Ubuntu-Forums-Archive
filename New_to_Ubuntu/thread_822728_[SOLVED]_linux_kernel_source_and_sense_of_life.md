---
title: "[SOLVED] linux kernel source and sense of life"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by mkarnicki on 2008-06-08
Wasup,

I'm trying to find the sense of my life. Could anybody tell me where can I find kernel source? Dang, I'm under /usr/src/my_kernel_version and all I see in every single folder are twp stand alone files Kconfig and Makefile. What's wrong? If I should download the sources to have them in /usr/src/kernel_version/ , please let met know how.

Thanks,
Mike, the Zen lamer

---

### Post by Sinkingships7 on 2008-06-08
Very confusing post, but I think you're looking for [http://www.kernel.org/](http://www.kernel.org/)

---

### Post by RequinB4 on 2008-06-08
[http://www.kernel.org/](http://www.kernel.org/)

Good luck, and have fun.

---

### Post by mkarnicki on 2008-06-08
@Sinkingships It was supposed to be a joke ;)

Thank you guys, I'll follow the link. I thought the sources where download-able via synaptic, since user sometimes recompile their kernels. Whatsoever, thanks again!

*meditating with the kernel code*

Mike

---

### Post by bodhi.zazen on 2008-06-08
You want the Ubuntu kernel source code ?

Install the "linux-headers"

```
sudo apt-get install linux-headers-`uname -r`
```

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-headers](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-headers)

---

### Post by crashsystems on 2008-06-08
Also, if you just want the tarball for the Ubuntu version of the kernel, you can run the following code:

```
apt-get source the-package-name
```

---

### Post by niteshifter on 2008-06-08
Hi,

There a few things about getting the sources from kernel.org: They're usually a couple releases ahead. Second, there are many to choose from. Third, the *ubuntus do not use a stock kernel, it has Canonical supplied patches.

Get it from the repositories. In Synaptic search for "linux-source". Install it and that will get you a nice large tarball of everything, patches included. You'll find it in the folder /usr/src. Also search for and install "linux-headers" - you'll probably want "linux-headers-generic" (unless you're after -rt or -server or -386, etc). They will also be placed in /usr/src.

Since I sniff a possible kernel builder, you also want these packages: "build-essential" and "kernel-package" OR just get "linux-kernel-devel" which includes the first two and tools.

And some advice: Backup - everything - before you deploy your new kernel. Or try it in a VM. Broken kernel = broken box, to the point of being completely unusable.

---

### Post by mkarnicki on 2008-06-08
Now **THAT** I call valuable replies! THANK YOU!

**bodhi.zazen**, **crashsystems** and **niteshifter** - these were very useful hints and instructions. I'm glad there was little more response on this topic. Now I'm packed with source, yay! Have a good day :)

---


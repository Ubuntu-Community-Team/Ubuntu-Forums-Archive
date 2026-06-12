---
title: "Kernel hacking"
date: 2007-05-11
forum: Programming Talk
---

### Post by nicholas22 on 2007-05-11
Hello

I have been playing around with the Minix source code and kernel for the last year.
I am wondering how can I do the same thing (edit, recompile, deploy) the kernel for Ubuntu 7.04. :guitar: 

I had a quick look in /usr/src and I only have two directories containing headers.
I also looked in the Synaptic Package Manager but can't find anything that rings a bell. 
(Perhaps linux-kernel-devel? not entirely sure)

To be more precise I'm not looking for instructions on how to make etc. (at the moment!)
 but rather where I can find/ how to download the source code.

Thanks for any help
:) 

Nicholas

---

### Post by Mathiasdm on 2007-05-11
The Linux kernel can be found at [http://kernel.org/](http://kernel.org/)

If you want a way to easily get different version, download it using git (the revision control software used by the kernel developers).
I have the source, but damn, it's so huge!

---

### Post by pmasiar on 2007-05-11
> **nicholas22 said:**
> I am wondering how can I do the same thing (edit, recompile, deploy) the kernel for Ubuntu 7.04. 

I would recomment *NOT* use standard kernel from kernel.org, but find guide to compile kernel for ubuntu. Look around at [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) - there is a guide how to download/compile kernel somewhere.

---

### Post by Ken_Lewis81 on 2007-05-11
I'd suggest the guides written by the Ubuntu Kernel Team at [wiki.ubuntu.com](wiki.ubuntu.com).

The key one is [KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild), and the list of articles about this area: [Wiki pages containing 'kernel' in the title](https://wiki.ubuntu.com/KernelCustomBuild?action=fullsearch&context=180&value=kernel&titlesearch=Titles)

There's a special branch of the kernel.org sources maintained by the Ubuntu Kernel team, and the guides suggest that you use git to get that, or the linux-source package.

Take care.
Ken.

---

### Post by nicholas22 on 2007-05-11
Thank you for your helpful replies,

I indeed tried with the official kernel that mathias suggested and I realized that there isn't very good integration. The kernel is not deployed properly (via "make install") on Ubuntu 7.04, so I had to hack the bootloader conf file and when that was done, some drivers were not loading properly. That left me with a CLI and no network (which was fun TBH :lolflag: but ideally I would like to have compiled a better kernel)

So it doesn't work very well, as pmasiar and Ken_Lewis81 indeed warned. So I think I will have to go through your suggested links guys, thanks again. :) 


Nicholas

---

### Post by FuturePast on 2007-05-11
```

sudo apt-get install linux-source kernel-package fakeroot
cd /usr/src/linux
make menuconfig
fakeroot make-kpkg clean
fakeroot make-kpkg --append-to-version=.fp kernel_image

```

Or something like that. Haven't done it in a while.

[http://newbiedoc.sourceforge.net/system/kernel-pkg.html#BUILD-KERNEL-PKG](http://newbiedoc.sourceforge.net/system/kernel-pkg.html#BUILD-KERNEL-PKG)

---

### Post by Prometheum on 2007-05-11
sudo apt-get source linux-source-`uname -r`, or use the [https://wiki.ubuntu.com/KernelGitGuide]("KernelGitGuide") to get the bleeding-edge source.

---


---
title: "Compile your own kernel..."
date: 2005-02-12
forum: Packaging and Compiling Programs
---

### Post by sniperd on 2005-02-12
I have been trying to compile my own kernel under ubuntu (I Have at least done over 50 in my days) but I keep getting errors like it cannot load the filesystem, it gives a bunch of modules.dep error, initrd, and cramfs errors and then kernel panics.

Now i have tried using initrd, not using it, using sources from kernel.org, sources from the apt repositories. using kpkg to roll my own, and just make bzImage , modules, modules_install, and make install and editing the grub menu.lst to boot using the initrd file and not.

I know debian(Ubuntu) uses some new cramfs junk in the initrd or to boot from, but what am i doing wrong? this is getting annoying...

---

### Post by mendicant on 2005-02-12
It's probably easiest to use make-kpkg and to start with a config from /boot and run make oldconfig on it before running make-kpkg (with --initrd).  This tends to mean that you use the kernel-source package.

---

### Post by evangelion on 2005-02-13
If you insist on building your own kernels from blank (or your own) config file without using The Debian Way (kmkpgk and all that jazz) here's a real quick guide on how I just did it not 5 minutes ago.  Since you're even trying to do this I'm going to assume you know pretty well what you're doing;

unpack your sources then to get a standard config file you can just 
**mv /boot/config-[something] /boot/config-[something].bk**

Now you'll have a normal config file, it won't have everything already set as a module so you'll need to know the things that must be selected. It's really importaint that you compile your file system supports in instead of as a module,  this can lead to "Unable to Mount root file system" kernel panics.

After you're set with configuring it  you can now **make; make bzImage modules modules_install**  do [i]not[i/] "make install"  I've never used it before,  maybe it's good, but I like to do as much on my own as possible, that way I'm sure it's done right (right = "my way", of course :))

Now from in your kernel source's directory you can **mv arch/i386/boot/bzImage /boot/bzImage-[something]**

Finally, add your new kernel to grub's menu.lst like so;

title           [title goes here]
root            (hd0,0)
kernel          /bzImage-[something] root=/dev/hda[X] ro

That's all I put,  there's a savedefault and boot aren't neccessary I guess.

If that still doesn't work, triple check your kernel's config,  make sure you've got your correct IDE chipset (and IDE disk support) compiled in there etc. And obviously, make sure you change all the [something]'s and the [X] in my guide to what they actually should be ;)

This should work and you'll be able to compile any kernel and patchset this way.  I know there are some guides on the wiki, but there are as many ways to comple a kernel as there are kernel patchsets to compile.

---

### Post by az on 2005-02-13
apt-get install build-essential linux-source-2.6 kernel-package initrd-tools

In Ubuntu, the kernel packages are named linux, as in linux-image, linux-source and so forth.

Copy the config for a working kernel from /boot to .config in your kernel source tree and then do

make-kpkg --revision=1 --append-to-version=-4-386 kernel_image (kernel headers are a good ides, too!)

If that kernel boots, then run make menuconfig (libncurses5-dev is needed)

---

### Post by macewan on 2005-02-16
[https://www.ubuntulinux.org/wiki/BeagleInstallHowto](https://www.ubuntulinux.org/wiki/BeagleInstallHowto)

the kernel section on this howto works

---


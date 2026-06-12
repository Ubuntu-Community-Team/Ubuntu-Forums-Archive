---
title: "Recompile Kernel, but only change 1 thing"
date: 2005-04-21
forum: Packaging and Compiling Programs
---

### Post by chapterthree on 2005-04-21
Hey All,

I want to re-compile my Kernel.  I am currently running 2.6.10-5-686-smp.  There is only one thing I need to change/add (want to add NTFS write support).  How can I recompile the kernel, but keep my current configuration and just change that one option?

I followed another post here to re-compile, but it seems like it stated with a standard config file, rather than the one that is currently being used.

Thanks

---

### Post by heimo on 2005-04-21
I don't know if this is answer to your question.. In /boot directory you can find files starting with config* - those are the configuration files for kernels installed in your system. Copy the correct one (check your kernel with uname -r) to /usr/src/linux/.config before starting configuration.
 
You could actually make the configuration change with text editor to that file, probably setting CONFIG_NTFS_RW to y. Compile as usual. If the source for kernel is newer than the configfile, you should *make oldconfig *and go through the new configuration options (probably just hitting enter = setting defaults).

---

### Post by chapterthree on 2005-04-22
Hey,

So I followed your instructions, I just copied the existing (working) config file, edited that one setting with a text editor, re-compiled, installed the new kernel, and I'm getting the following error at boot:

```
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)
```

Any ideas?

---

### Post by fackamato on 2005-04-22
[QUOTE=chapterthree]Hey,

So I followed your instructions, I just copied the existing (working) config file, edited that one setting with a text editor, re-compiled, installed the new kernel, and I'm getting the following error at boot:

```
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)
```

Any ideas?[/QUOTE]

Did you make a new initrd, and add the appropriate settings to grub?

---

### Post by chapterthree on 2005-04-22
> Did you make a new initrd, and add the appropriate settings to grub?

Honestly I'm not sure.  I was following some instructions, and after I edited the .config file, I did the following:

```
sudo make-kpkg --append-to-version=kevkernel --revision=001 kernel_image
sudo dpkg -i kernel-image-2.6.10kevkernel_001_i386.deb
```
Then I reboot, choose my kernel, it starts to boot, gets to the "boot" and "savedefault" lines, then kicks out that error.

I have been doing some research, and it sounds like an issue with initrd, but I'm kind of a n00b and recompiling, so not sure how to make a new one, if you have any suggestions or step by step instructions, that would be great.

Thanks

---

### Post by chapterthree on 2005-04-22
Well, I've been doing more research, and found a thread where user had same error, and did the following command, so I did this, but there was no change.

```
$ sudo mkdir /lib/modules/2.6.10kevkernel/boot/
$ sudo cp -a /lib/modules/2.6.10kevkernel/kernel/security/capability.ko \
/lib/modules/2.6.10kevkernel/boot/
$ sudo mkinitrd -o /boot/initrd.img-2.6.10kevkernel 2.6.10kevkernel
```

It did create a new initrd.img in the boot directory, but still no go.

---

### Post by chapterthree on 2005-04-22
Viiiiiictory :)

So yeah, I didn't realize I had to specifically tell Grub to use that new initrd, so I had to add the following line to my menu.lst right underneath the kernel line:
```
initrd          /boot/initrd.img-2.6.10kevkernel
```

So yes, fackamato's suggestion was exactly what needed to be done, but me being a n00b had to find out exactly what that meant and how to do it, but thank you for guiding me in the right direction :)

---

### Post by fackamato on 2005-04-22
No problem! Glad you got it working.

---

### Post by timmir on 2007-03-01
For what's it worth, I;ve had great success with the ntfs-3g program.  Since it's based on fuse you don't have to recompile the kernel to add it.  Once installed I just change my fstab entries from ntfs to ntfs-3g and the work great.  Only bad side, is if the ntfs partition was shut down incorrectly, it won't mount while the older driver will.  I'm glad you're learning about kernel building.  I'm trying to get the dsdt patck into the feisty kernel and this thread helped me.

---


---
title: "kernel packages"
date: 2009-11-16
forum: Packaging and Compiling Programs
---

### Post by Piscium on 2009-11-16
Well, I am using Ubuntu Karmic and suspend is OK but not perfect, so I thought I would try to build the kernel. I followed the gist of these instructions:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

Building 2.6.31.6 from sources at kernel.org succeeded. I booted from it, and so far have found no issues. I have some questions, though.

Looking at \boot on my pc, I have 3 vmlinuz, my custom one plus two from Ubuntu. I also have 3 config's and 3 System.map's, all about the same size. So far so good.

However I have only 2 abi's and 2 vmcoreinfo's - I am missing a custom one. Is that a problem?

Also while initrd for the Ubuntu versions takes 7.5 MBytes, my custom one takes 63.4 MBytes.

Does anybody have an explanation for the above?

By the way, I also tried to build 2.6.32-rc7 and it failed. There were some build errors, but as far as I can tell they are due to kernel issues rather than something wrong with my PC. I am planning to try building 2.6.32 again once there is an official release.
 	
Thanks.

---

### Post by Yellow Pasque on 2009-11-18
Did you configure your kernel to include debugging symbols? That will add to its size significantly.

> However I have only 2 abi's and 2 vmcoreinfo's - I am missing a custom one. Is that a problem?
No.

Building kernels is interesting and good practice, but when you get tired of the tediousness: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Piscium on 2009-11-19
Hi Temüjin,

You are right, it was the debugging symbols. They were included inadvertently. This FAQ explains it:
[https://wiki.ubuntu.com/KernelTeam/FAQ]("https://wiki.ubuntu.com/KernelTeam/FAQ")

So I rebuilt the kernel with CONFIG_DEBUG_INFO unset, and the new initrd was about the same size as the Ubuntu generic. Interestingly, rebuilding without symbols had other consequences: the size of the image deb file was reduced by about 90%, from 376 MBytes to 29.3; the space taken on disk by the kernel build directory was reduced from 4.3 GBytes to 716 Mbytes; and the time that it took to build the kernel was reduced by 25%. Amazing.

So I am happy with my custom kernel, it seems faster, and Firefox seems to be leaking less memory, which was unexpected.

I will try to run a few tests over the next days to compare the kernels. I have already installed Phoronix.

About vmcoreinfo, it looks like it can be created by makedumpfile. My Grub2 is configured as not quiet, so I see text flashing up the screen fast when booting. It looks like Apparmor is not starting with my custom kernel. This might be related to the missing vmcoreinfo. Who knows.

Incidentally, I am also using my own build of Grub2 with sources from the Grub website, because Karmic Grub2 (1.97 beta4) does not work well on my PC.

So thanks for letting me know that vmcoreinfo and abi are not critical, I will sleep better tonight! :)

---


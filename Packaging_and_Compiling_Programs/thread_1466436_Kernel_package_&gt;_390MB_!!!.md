---
title: "Kernel package &gt; 390MB ???!!!"
date: 2010-04-30
forum: Packaging and Compiling Programs
---

### Post by benj.david on 2010-04-30
Hi all,
I'm trying to build a custom kernel.

Today, I tried a very simple thing :
- I donwload & install linux-image-2.6.31-14-virtual (to get the config file)
- I download its sources.
- I copy the config file to the source tree :
      cp /boot/config-2.6.31-14-generic-pae /usr/src/linux-source-2.6.31/.config
- I build the kernel package the debian way (make menuconfig, make-kpkg, etc.)

After some times, the "image" is built, but it is really really big :
-rw-r--r--  1 root src  6,1M 2010-04-30 12:51 linux-headers-2.6.31.4-custom-virtual_2.6.31.4-custom-virtual-10.00.Custom_i386.deb
-rw-r--r--  1 root src  394M 2010-04-30 12:49 linux-image-2.6.31.4-custom-virtual_2.6.31.4-custom-virtual-10.00.Custom_i386.deb

I don't get it : I use the same sources and config file that the ones used by the ubuntu team to build this package ?!

Many thanks for your help,
ben

---


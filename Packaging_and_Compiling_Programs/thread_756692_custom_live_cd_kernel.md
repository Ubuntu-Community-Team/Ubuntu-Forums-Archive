---
title: "custom live cd kernel"
date: 2008-04-16
forum: Packaging and Compiling Programs
---

### Post by BigCdaAnswer3 on 2008-04-16
Hey all I'm a little stuck doing a swap of the feisty live cd kernel. Initially I'm just trying to grab the linux-source-2.6.20 package, enable squashfs and pop it in as a replacement. I'm using make-kpkg with the --initrd option, but it seems that whenever I install the deb and the ramdisk gets generated, it's missing the necessary squashfs support -- so whenever the live cd boots, it fails to mount the root file system and drops me into a busybox shell. 

I was told in #ubuntu-kernel that I don't need to mess with the udebs because I'm not doing an alternate install cd...so I'm not sure what else to try. All you kernel gurus out there any help would be awesome!!!

---


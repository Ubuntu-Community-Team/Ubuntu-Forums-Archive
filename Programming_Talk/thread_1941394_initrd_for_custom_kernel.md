---
title: "initrd for custom kernel"
date: 2012-03-15
forum: Programming Talk
---

### Post by MDL1983 on 2012-03-15
Hello,

Complete Linux novice here, so please bare with me. I have successfully built a custom kernel (based off Linux Next), but I am unable to boot into it. I get to the password-entry screen, but can go no further because my keyboard and mouse do not load; I can't type or do anything. I suspected that this is because I didn't have a initrd set up to load in my grub.cfg, but when I generate one using mkinitramfs, the same thing happens. My questions:

1. Since my keyboard and mouse drivers are not loading (the video is low-res too, hinting at some default video driver), am I correct to think that the problem is with the initrd file? Can someone explain (guess) what exactly is happening here?

2. Is the lack of (or incorrect) initrd file really the source of the problem? Is it possible that I did something wrong when compiling the kernel? (I used the oldconfig from a working kernel build, and the only differences between the custom kernel and LinuxNext are in the USB3 driver).

3. Can anyone provide any solutions? Is there a special way to build the mkinitrawfs file?

Thank you!

---

### Post by CynicRus on 2012-03-15
[http://manpages.ubuntu.com/manpages/intrepid/man8/mkinitramfs.8.html]("http://manpages.ubuntu.com/manpages/intrepid/man8/mkinitramfs.8.html") - man mkinitramfs, [http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/]("http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/") - man fresh kernel build.

---


---
title: "After selecting ubuntu in grub menu, boots to black screen"
date: 2015-01-18
forum: New to Ubuntu
---

### Post by Eugene_Lee on 2015-01-18
I tried changing a couple of boot commands, "quiet splash" to "nomodeset".

Here's the result when I try to reboot it.
[http://i.imgur.com/cKj6mzR.jpg](http://i.imgur.com/cKj6mzR.jpg)

---

### Post by grahammechanical on 2015-01-18
I do not think that replacing quiet splash" with "nomodeset." would do that. I see EXT4-fs error again and again. EXT4 is the file system. My guess is that there is something wrong either with the hard disk or the file system on the hard disk. You can try

1) Loading Recovery mode and then at the Recovery menu select fsck - check all file systems.
2) Run the Ubuntu installation DVD/USB and at the first purple screen press Enter. At the second screen select the language (English default) and at the underlying screen select Check disc for defects.

You may not be able to load Recovery mode because Recovery mode depends upon Linux being loaded. So, you may see these same errors before you get to a Recovery menu.

By the way, all nomodeset does is instruct Linux (Xserver) not to set the video mode. It is useful if there are problems between the Linux kernel and the proprietary video driver or in identifying the optimum resolution of the monitor. It may get us to a working desktop where we can try to fix things. It cannot fix what is wrong with your file system.

Regards.

---


---
title: "HELP:ERROR when i boot the compiled Kernel"
date: 2006-02-14
forum: Programming Talk
---

### Post by sirmoreno on 2006-02-14
i compiled the linux-2.6.15.4 and i added to the Grub:

title Custom Linux Kernel 2.6.15.4
root (hd0,1)
kernel /boot/bzImage ro root=/dev/hda0 hdc=ide-scsi

and when i boot i get:
VFS: Cannot open root device "hda0" or unknown - block(0,0)
after that a Kernel panic and it just Stops
i tryed to chage it too hda1 or hda2 but it didn't work
Any Help will do :?

---


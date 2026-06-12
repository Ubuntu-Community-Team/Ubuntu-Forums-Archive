---
title: "Broadcom firmware automatic installer"
date: 2007-03-08
forum: Outdated Tutorials &amp; Tips
---

### Post by alecjw on 2007-03-08
I've made a simple script to automatically install the broadcom firmware on dapper, edgy and feisty without the need for an internet connection (except to downlaod the installer).

I've made a floppy disk image and an archive. If you want to burn it to a floppy, just download floppy.img.bz2, extract the archive and then burn it using the command:
```
dd if=floppy.img of=/dev/fd0
```

If you want to user it on somethign else (for example, a pen drive), just downlaod floppy.tar.bz2 and extract it to your pen drive or the source disk.



Put the disk into the computer which you want to install the firmware on and run the install file. There's also a readme on it which tells you how to use it.

---


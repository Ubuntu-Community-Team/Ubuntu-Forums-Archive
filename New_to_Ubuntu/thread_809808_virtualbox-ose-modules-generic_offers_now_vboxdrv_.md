---
title: "virtualbox-ose-modules-generic offers now vboxdrv in /dev/"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by kevCast on 2008-05-27
Hello. When I tried to install the package virtualbox-ose-modules-generic, I receive an error message that says the vboxdrv could not be installed. Looking through /dev/, I can't seem to find the driver at all. Is the package shooting blanks? Has this happened to anyone else? Thank you for any and all help.

---

### Post by luisjorge on 2008-05-27
Hi! I have the same problem. It's related to the last kernel update, whichwent from version 2.6.24-16 to 2.6.24-17. The problem is that the VirtualBox modules are still for -16, and haven't been released for -17 version, so in the meantime you can press "esc" when the countdown shows up when booting your computer, and select the 2.6.24-16 kernel, that way you can use virtualbox, at least until they release the -17 version modules. Here's a bit more info: [http://ubuntuforums.org/showthread.php?t=808269&highlight=vitualbox+ose+kernel+modules&page=2](http://ubuntuforums.org/showthread.php?t=808269&highlight=vitualbox+ose+kernel+modules&page=2)

Hope this helps!

Luis Jorge.

---

### Post by Delever on 2008-05-27
You can enable PROPOSED (pre-release) updates in Software sources, update ONLY vbox modules, then disable PROPOSED updates. Solved? :)

---


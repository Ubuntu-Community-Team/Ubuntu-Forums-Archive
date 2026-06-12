---
title: "the use of &quot;rmmod&quot;"
date: 2006-06-22
forum: Programming Talk
---

### Post by eqi013 on 2006-06-22
after i use the "insmod" , I can't use the "rmmod" to remove my kernel driver. the problem is :
root@ubuntuDavid:~# lsmod
Module                  Size  Used by
usbfx                   4552  -
root@ubuntuDavid:~# rmmod usbfx
FATAL: Kernel does not have unload support.

how can i deal with it??
Thanks!

---

### Post by ynef on 2006-06-22
Either compile a kernel that can unload modules, or accept that the module will remain loaded until you reboot.

---

### Post by LordHunter317 on 2006-06-22
Even with a kernel that can unload modules (his very well may be able to) modules can mark themselves permanent and can never be removed.

---


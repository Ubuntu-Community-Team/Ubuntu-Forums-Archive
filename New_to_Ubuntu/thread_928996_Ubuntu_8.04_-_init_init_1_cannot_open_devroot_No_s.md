---
title: "Ubuntu 8.04 - /init: /init: 1: cannot open /dev/root: No such device or address"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by forigato on 2008-09-24
:lolflag: Hello all,

Ubuntu 8.04
Dell PowoeEdge 2650

Upon rebooting the system after the successful installation I was presented with a busybox shell. Error messages on boot include:

"Begin: Mounting root file system... ...
Begin: Running /scipts/local-top ...
Done.
/init: /init: 1: cannot open /dev/root: No such device or address
Begin: Running /scripts/local-premount ...
Done." ...
"Target filesystem doesn't have /sbin/init"

What is happening? have any idea?

---

### Post by Crafty Kisses on 2008-09-24
Boot from a LiveCD, mount your / at for example /media/root, then do
```
sudo chroot /media/root
sudo aptitude reinstall ubuntu-minimal
```
Show us what the results are.

---


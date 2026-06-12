---
title: "Why update-initramfs -c -k 3.13.0-79 command results like this in Ubuntu 14.04"
date: 2016-03-03
forum: New to Ubuntu
---

### Post by pavlushka on 2016-03-03
The following command 
sudo update-initramfs -c -k 3.13.0-79 results the following:
  
grep: /boot/config-3.13.0-79: No such file or directory WARNING: missing /lib/modules/3.13.0-79 Device driver support needs thus be built-in linux image! depmod: ERROR: could not open directory /lib/modules/3.13.0-79: No such file or directory depmod: FATAL: could not search modules: No such file or directory depmod: WARNING: could not open /tmp/mkinitramfs_hMx6Bi/lib/modules/3.13.0-79/modules.order: No such file or directory depmod: WARNING: could not open /tmp/mkinitramfs_hMx6Bi/lib/modules/3.13.0-79/modules.builtin: No such file or directory
  
any idea?

---

### Post by Bashing-om on 2016-03-03
pavlushka; Well;

A couple of ideas ..
1) out of disk space and the new -79 kernel did not fully install ?
what returns:
```

df -h
df -i
ls -al /usr/src/
ls -al /lib/modules/

```
As advised by the package manager (C)reate the new initramfs, and the needed modules are not present.

2) linux-generic and the related headers are not installed ?
what is installed ?
```

dpkg -l | grep linux-

```

It is a puzzle;
[INDENT][INDENT]we need all the pieces to put it all together
[/INDENT][/INDENT]

---


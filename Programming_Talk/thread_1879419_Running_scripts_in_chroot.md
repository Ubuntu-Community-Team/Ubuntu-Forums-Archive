---
title: "Running scripts in chroot"
date: 2011-11-11
forum: Programming Talk
---

### Post by sandyd on 2011-11-11
How would I get a script to run commands in a chroot?

---

### Post by MadCow108 on 2011-11-11
man chroot
> chroot [OPTION] NEWROOT [COMMAND [ARG]...]


```
sudo chroot precise-amd64/ ls
bin   dev  home  lib64	mnt  proc  run	 selinux  sys  usr
boot  etc  lib	 media	opt  root  sbin  srv	  tmp  var

```

---


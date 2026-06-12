---
title: "Ubuntu live-build, help needed."
date: 2012-09-18
forum: Programming Talk
---

### Post by ryanrio95 on 2012-09-18
Hi there.

Does anyone know how i can make the default Ubuntu 12.04 iso with the live-build scripts?

I think it isn't just:
```
lb clean
lb config
lb build
lb clean
```

And i have a problem that /dev and the other things that should be mounted with the lb build script doesn't unmount.

Edit: This is the problem.
```
[2012-09-18 20:50:02] lb_chroot_live-packages 
Reading package lists...
Building dependency tree...
Reading state information...
P: Begin unmounting filesystems...
```

Thanks in advance.

---


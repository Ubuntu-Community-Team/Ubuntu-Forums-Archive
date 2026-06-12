---
title: "libvirt with c/c++ error"
date: 2012-06-25
forum: Programming Talk
---

### Post by gerger09 on 2012-06-25
I tried compiling my code using gcc and it gave me an error
```
error fatal error: libvirt/libvirt-qemu.h: No such file or directory
```

How do I fix this? Did I forget to install something? I'm using Fedora 17.

---

### Post by 11jmb on 2012-06-26
How did you install this? I'm not as familiar with Fedora as I am with Ubuntu, but in Ubuntu there is often a standard version and a -dev version which contains the headers.

My guess is that you installed the libraries but not the headers

---


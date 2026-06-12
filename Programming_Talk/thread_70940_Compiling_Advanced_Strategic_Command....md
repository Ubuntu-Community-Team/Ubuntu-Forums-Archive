---
title: "Compiling Advanced Strategic Command..."
date: 2005-10-01
forum: Programming Talk
---

### Post by kudu on 2005-10-01
Hi,

I was running make and received the following error message:

/usr/bin/ld: cannot find -lvga

Can anyone please tell me where I might find this missing library file ?

Thanks!
kudu

---

### Post by lithorus on 2005-10-17
```
# apt-file search libvga.so
libsvga1: usr/lib/libvga.so.1
libsvga1: usr/lib/libvga.so.1.4.3
libsvga1-dev: usr/lib/libvga.so
svgalib1-libggi2: usr/lib/libvga.so.1
svgalib1-libggi2: usr/lib/libvga.so.1.99.4

```
I would go for the libsvga1-dev since the svgalib1-libggi2 seems to be some kind of wrapper.

---


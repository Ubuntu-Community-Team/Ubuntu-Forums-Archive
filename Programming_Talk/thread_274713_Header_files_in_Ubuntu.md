---
title: "Header files in Ubuntu"
date: 2006-10-10
forum: Programming Talk
---

### Post by mavix on 2006-10-10
Where will I find the header files for GCC?

---

### Post by ape on 2006-10-10
Which particular header files are you looking for?  I'd start with installing the libc6-dev and whatever kernel-headers-* package matches your current kernel version.

Usually, any header files for a particular application are contained in that applications *-dev.deb package.

---

### Post by loell on 2006-10-10
if you have properly installed c development tools
by installing like

sudo aptitude build-essential

then you can find *.h files in
/usr/include
or
/usr/local/include

---


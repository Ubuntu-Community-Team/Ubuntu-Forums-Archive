---
title: "error while compiling kernel"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by sharks on 2008-05-20
when i compiled 2.6.25.4 there was an error at the very end> dpkg-deb: building package `linux-image-2.6.25.4' in `../linux-image-2.6.25.4_386_i386.deb'.
dpkg-deb: control directory has bad permissions 2755 (must be >=0755 and <=0775)
make[1]: *** [debian/linux-image-2.6.25.4] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.25.4'
make: *** [binary/linux-image-2.6.25.4] Error 2

because of this i did not get the deb files

---

### Post by Eclipse. on 2008-05-20
I recomend using kernelcheck for compiling kernels, great little spp with a nice gui.

See here: kcheck.sourceforge.net

Also this really isnt the right section, building kernels isnt really "Absolute Beginner Talk".

---

### Post by Nepherte on 2008-05-20
As the error suggests, the map you are currently working in has wrong permissions. Try changing it to 755.

---

### Post by sharks on 2008-05-20
How to change it to 755?

---


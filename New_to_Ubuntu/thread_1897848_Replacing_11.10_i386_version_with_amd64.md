---
title: "Replacing 11.10 i386 version with amd64"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by pmpgrant on 2011-12-20
I mistakenly installed the i386 version of 11.10 on my AMD64 box and began installing a number of packages and apps.  Is there any way I can replace (upgrade)the i386 version with the amd64 version with having to do a completely new install, and at the same time preserve the already existing packages and apps?
-Paul

---

### Post by BC59 on 2011-12-20
I found [this]("http://http://www.v13.gr/blog/?p=11") but looks so complicated that I suggest you to do a fresh install with the 64bits.

---

### Post by MartijnNL on 2011-12-20
Or just leave it as it is. As it will work fine. Are you using it for anything which requires the bit of efficiency bonus a 64bit version will bring?

---

### Post by lechien73 on 2011-12-20
Hi Paul & welcome to the forums,

Unless you have more than 4Gb RAM, you probably won't notice much of a benefit from switching to 64-bit.

It is technically possible to upgrade, but when I decided to replace my i386 installation with amd64, then it was easier to back up my home partition and completely re-install.

---

### Post by pmpgrant on 2011-12-20
Thanks to all. I can't use i386 because one of my apps is a highly optimized gfortran routine (Jacobi diagonalization) that gives segmentation faults (memory overuns) on an i386 architecture...requires x64 (AMD64) which runs just fine.  Anyone else had this problem?

---

### Post by MartijnNL on 2011-12-20
In that case do you have your /home on a separate partition? That would allow you to at least save your settings when re-installing. You will probably have to choose manual partitioning to achieve that. Make sure not to reformat the /home partition in that case. And also make sure to use the same username as you have now.

---

### Post by 3rdalbum on 2011-12-20
> **MartijnNL said:**
> In that case do you have your /home on a separate partition? That would allow you to at least save your settings when re-installing.

Since 2009, the Ubuntu installer has preserved the contents of /home even when it's on the same partition as /.

The installer for 11.10 has the option of "Upgrade" - it's a fresh install, but it keeps your /home and also makes note of what packages you have installed. After installing Ubuntu it will download and install the updated versions of your old packages.

No idea if this will work for an i386-to-AMD64 conversion, but even if not you can still use the Manual partitioning method and it will preserve /home; just make sure you do NOT format /

Hope this has helped you.

---

### Post by MartijnNL on 2011-12-20
> **3rdalbum said:**
> Since 2009, the Ubuntu installer has preserved the contents of /home even when it's on the same partition as /.

The installer for 11.10 has the option of "Upgrade" - it's a fresh install, but it keeps your /home and also makes note of what packages you have installed. After installing Ubuntu it will download and install the updated versions of your old packages.

Hmm, I didn't know about either option. That's very nice indeed.

---


---
title: "error message on startup"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by medphys17 on 2013-10-09
Hi all,

Keep getting this error message on startup (Buffer I/O error on device zram0, logical block 504937) can anyone tell what it means and how to fix it?  I am rinning Ubuntu 12.04 64 bit.  I also have not been able to log in to Gnome classic as before.  I can log in with unity.

Thank you

---

### Post by heir4c on 2013-10-09
Have you installed Zram by yourself? If not, I search for it and now zram is a module in the kernel from version 3.2. and I read they think it's a bug. So, I think in the future it will be solved. 
more info: [https://en.wikipedia.org/wiki/ZRam](https://en.wikipedia.org/wiki/ZRam)

---

### Post by philinux on 2013-10-09
> **medphys17 said:**
> Hi all,

Keep getting this error message on startup (Buffer I/O error on device zram0, logical block 504937) can anyone tell what it means and how to fix it?  I am rinning Ubuntu 12.04 64 bit.  I also have not been able to log in to Gnome classic as before.  I can log in with unity.

Thank you

Seems like an active bug. [https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1217189](https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1217189)

---


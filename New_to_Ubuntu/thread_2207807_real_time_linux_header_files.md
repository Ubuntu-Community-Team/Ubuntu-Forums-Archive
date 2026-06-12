---
title: "real time linux header files"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by aashik2 on 2014-02-25
are there seperate header files for rt linux like rtl.h etc, for kernel v 3.2 rt1? If so do we need to download them from somewhere?
Thank you

---

### Post by tgalati4 on 2014-02-25
You need to download the linux kernel headers for the baseline kernel that you are trying to compile.  I don't believe there are separate real time headers.  Are you following a [tutorial]("https://help.ubuntu.com/community/Kernel/Compile")?

---

### Post by aashik2 on 2014-02-25
Yes am basically following examples, but most of them have an header file named rtl.h , which is not present in my library.

---

### Post by tgalati4 on 2014-02-26
Oh, well then, you need to find it.  I've compiled kernels for undervolting and different scheduling, but not pre-empt real time.  So search around the web and see if you can find an older rt header and try to use that.

---

### Post by aashik2 on 2014-02-26
ya , Thanks for your help !!!

---

### Post by aashik2 on 2014-03-05
It seem that header file used come only with kernel v2.4.x.

---


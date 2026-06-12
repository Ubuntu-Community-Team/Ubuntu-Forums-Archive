---
title: "'Include' Not Found"
date: 2008-03-25
forum: Packaging and Compiling Programs
---

### Post by FlyingIsFun1217 on 2008-03-25
Hey!

Using Hardy, trying to compile the Torque Game Engine, I get the following error:

> 
/home/[user]/Desktop/TGE_1_5_2/mk/conf.GCC4.LINUX.mk: line 1: include: command not found


Is this a missing dependency or something? Previous compile always seemed to work fairly flawlessly (given that I had the need lib's).

Thanks!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-03-25
22 views, and nobody has an idea?

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-03-26
'Aye' if this should be moved to Development->Hardy...

FlyingIsFun1217

---

### Post by Zugzwang on 2008-04-01
It appears to me as you are trying to execute a file which isn't meant to be executed. Did you follow the compilation procedure as written in the README file (or whatever)? Usually, this is running "./configure" and then "make".

---


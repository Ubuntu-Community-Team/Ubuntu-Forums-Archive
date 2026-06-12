---
title: "Linux-&gt;Nasm-&gt;Flush ports"
date: 2010-07-09
forum: Programming Talk
---

### Post by yousafsajjad on 2010-07-09
Hi,

I am using the following code to flush port:

 in      al, 081h
 out     081h, al     

but it is giving me segmentation fault. Does anyone how I can do it.

---

### Post by xb12x on 2010-07-09
If you're doing this from inside a Linux User-level application you will cause an exception/fault.  Linux is a protected O.S. which means you cannot access hardware directly from a User-level application. Your code does not have the necessary permissions.

If you want to access hardware your application must call a driver (System-level code).

---

### Post by yousafsajjad on 2010-07-10
yeah you are right .. i am calling an assembly function from C. So I need to get permission to that port using ioperm() first and than it works.

---


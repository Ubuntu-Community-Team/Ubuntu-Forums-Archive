---
title: "link error, libSM to libuuid, ubuntu 10.04"
date: 2010-05-14
forum: Programming Talk
---

### Post by gaoyicn on 2010-05-14
Dear all,


When I'm building a software I got the link error as:
/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/libSM.so:
undefined reference to `uuid_generate@UUID_1.0'
/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/libSM.so:
undefined reference to `uuid_unparse_lower@UUID_1.0'

I'm running ubuntu 10.04 64bit and I have installed
libuuid1
uuid-dev
uuid-runtim

libsm6
libsm-dev


When I do "ldd libSM.so" in /usr/lib/ I got:
       linux-vdso.so.1 =>  (0x00007fff6f9d2000)
       libICE.so.6 (0x00007f63004e7000)
       libuuid.so.1 => /lib64/libuuid.so.1 (0x00007f63002e1000)
       libc.so.6 => /lib64/libc.so.6 (0x00007f62fff5f000)
       /lib64/ld-linux-x86-64.so.2 (0x00007f630090d000)
and libuuid.so.1 is in /lib64/

So everything looks okay to me....

The software I was trying to build, though I don't think this matters,
is 3D Slicer (slicer.org)

Could I have any hint?

Thanks in advance!

Best,
yi

---

### Post by mmix on 2010-05-14
libice-dev

---

### Post by gaoyicn on 2010-05-14
> **mmix said:**
> libice-dev

but libice-dev has already been installed .....:(

---

### Post by mmix on 2010-05-14
[http://jira.secondlife.com/browse/SNOW-606](http://jira.secondlife.com/browse/SNOW-606)

---

### Post by Some Penguin on 2010-05-14
Did you actually specify the libraries in the linking statement?

---


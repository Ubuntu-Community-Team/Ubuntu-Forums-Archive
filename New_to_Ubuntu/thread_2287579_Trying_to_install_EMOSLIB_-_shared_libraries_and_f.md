---
title: "Trying to install EMOSLIB - shared libraries and fortran trouble"
date: 2015-07-20
forum: New to Ubuntu
---

### Post by leo_br_hidro on 2015-07-20
When trying to install the EMOSLIB with the following command: 
```
leonardo@leoHP:~/builds/libemos/build$ cmake

```
I get this error:
```
Inconsistency detected by ld.so: dl-version.c: 224: _dl_check_map_versions: Assertion `needed != ((void *)0)' failed!
```

For which I couldn't find any guidance online.

---

### Post by steeldriver on 2015-07-20
What is your Ubuntu version? What is the exact EMOSLIB version that you are trying to build?

Does the system have an nvidia graphics card? There seems to be some indication on the web that the error is related to nvidia's libGL.so

---

### Post by leo_br_hidro on 2015-07-21
Hello there, here's my system info:
Operating system: ubuntu 14.04 LTS
Memory: 3,8 GiB
Processor: Intel Core 2 Duo CPU P7350 @2.00GHz x2
Graphic: Mobile Intel GM45 Express Chipset
System type: 64-bit

I am trying to install EMOS lib version 4.0.7, the latest one.

So I don't think there's a Nvidia graphics card. I'll try to find that ld.so file or that libGL.so .

---


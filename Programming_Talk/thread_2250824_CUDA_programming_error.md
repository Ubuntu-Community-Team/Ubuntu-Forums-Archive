---
title: "CUDA programming error"
date: 2014-10-31
forum: Programming Talk
---

### Post by Constantinus_Spin on 2014-10-31
Hello, i am trying to program in CUDA.  I took a code that compiles and is executed in windows and when i tried to compile it in ubuntu, it was ok. The execution, however, had a problem. I got the following error message:

FATAL: Error inserting nvidia_340 (/lib/modules/3.2.0-37-generic/updates/dkms/nvidia_340.ko): No such device

What could be the problem???

---

### Post by ofnuts on 2014-10-31
Have you got a file "/lib/modules/3.2.0-37-generic/updates/dkms/nvidia_340.ko" on your system? You may be missing a specific driver. I have zero CUDA experience, but AFAIK .ko file are kernel extensions, and normally come with some specific packages (the ones I have are for VirtualBox)

---


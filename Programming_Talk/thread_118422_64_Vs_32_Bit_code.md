---
title: "64 Vs 32 Bit code"
date: 2006-01-17
forum: Programming Talk
---

### Post by mdh on 2006-01-17
Hi,

I have an amd64 box and I am running ubuntu breezy. Does invoking gcc on amd64 build a 64 bit executable by default or should it be instructed to do so by passing the appropriate compiler flag ?. More specifically, I do I tell if *configure make make install* chain (with no extra options) of a source package that is building a 64-bit program/library as opposed to a 32-bit.

Thanks,
mdh

---

### Post by Viro on 2006-01-17
If you have a 64 bit machine, by default it should be building 64 bit binaries. I think you need to pass the flag -m32 if you want it to generate 32 bit binaries.

---


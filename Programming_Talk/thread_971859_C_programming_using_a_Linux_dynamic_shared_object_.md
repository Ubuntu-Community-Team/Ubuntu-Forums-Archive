---
title: "C programming: using a Linux dynamic shared object (.so) library?"
date: 2008-11-05
forum: Programming Talk
---

### Post by khughitt on 2008-11-05
Hi all,

I don't have too much experience programming C, and have never had to link to dynamic libraries on Linux before. I installed such a library though via aptitude, and it now sits in /usr/lib.

Can anyone please explain what I need to do to be able to start calling methods from the library? I've tried updating ldconfig to make sure it sees it, and also tried using "-l" in gcc, but it cannot find it.

The library I'm attempting to use is called "OpenJpeg." It is available in the 8.10 repos:

```
sudo apt-get install libopenjpeg2
```

And has documentation online at [http://www.openjpeg.org/libdoc/group___j_p2.html](http://www.openjpeg.org/libdoc/group___j_p2.html).


Any suggestions? Any help would be greatly appreciated.

Thanks!

---

### Post by leg on 2008-11-05
You need the header files for it for when you compile and then also to link to the lib when you build the binary. If the headers are in a standard path you should be ok but you will need to link the lib into your bin. -lopenjpeg2 for linking.



[GCC Book]("http://www.network-theory.co.uk/docs/gccintro/").

---

### Post by mali2297 on 2008-11-05
The header file openjpeg.h is in the development package **libopenjpeg-dev**.

---

### Post by WW on 2008-11-05
> **pwnedd said:**
> 
 I installed such a library though via aptitude, and it now sits in /usr/lib.

Can anyone please explain what I need to do to be able to start calling methods from the library? I've tried updating ldconfig to make sure it sees it,

If you installed it from the Ubuntu repositories via aptitude, and it is sitting in /usr/lib, there is no need to run ldconfig.
> **pwnedd said:**
> 
 and also tried using "-l" in gcc, but it cannot find it.

It would help if you showed *exactly* how you "tried using "-1"", and show the actual error that you get.  You may have simply used -l incorrectly.  In this case, the option to use is **-lopenjpeg**.

---


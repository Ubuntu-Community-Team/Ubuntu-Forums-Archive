---
title: "How do you guys distribute your apps?"
date: 2008-09-08
forum: Programming Talk
---

### Post by StOoZ on 2008-09-08
in linux?
im having hard times with CMake , seriously , Im having a lot of fun developing app's in linux , in C++ , and but when it comes to deployment , packaging and stuff , its really a pain in the a$$.
so what about you?

---

### Post by mssever on 2008-09-08
> **StOoZ said:**
> in linux?
im having hard times with CMake , seriously , Im having a lot of fun developing app's in linux , in C++ , and but when it comes to deployment , packaging and stuff , its really a pain in the a$$.
so what about you?
Most C and C++ projects use make with GNU autotools. I have very little experience with them, though.

---

### Post by days_of_ruin on 2008-09-08
Bazaar + LaunchPad

---

### Post by kknd on 2008-09-08
Plain Makefiles. For distribution I create "native" packages, like .pkg.tar.gz or .deb.

---

### Post by LaRoza on 2008-09-08
tarballs, with a readme.

---

### Post by StOoZ on 2008-09-09
@kknd

when u say plain makefiles , you mean those with configure , or only a makefile?

I started using CMake , and I wont say it is going as smooth as I thought.

---

### Post by SeanHodges on 2008-09-09
CMake is my personal favourite. For the smaller programs I might just provide a BASH script and a README. 

What problems are you having with CMake? If you've asked questions on other threads just post the links here and I'll see if I can help :)

---

### Post by cb951303 on 2008-09-09
I'd choose CMake over GNU Make anytime :)

---

### Post by scourge on 2008-09-09
Plain C/C++: source code + Makefiles for Linux/OSX/etc., and nmake file for MSVC++
C++/Qt: source code + Qmake project file
C++/wxWidgets: source code + bakefile

---


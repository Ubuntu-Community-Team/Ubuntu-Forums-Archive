---
title: "Cannot Find linOpenCV: Ubuntu 11.10"
date: 2011-11-18
forum: Programming Talk
---

### Post by OtagoHarbour on 2011-11-18
I am using Ubuntu 11.10.  I have noticed that OpenCV is part of the default system and I would like to write a C++ program that uses OpenCV.  However, I cannot find libOpenCV, or any variation thereof, on my system.  I tried

```
find / -name "libopencv*" -print 2>junk
```and
```
find / -name "libOpenCV*" -print 2>junk
```but no results were returned.  As a consequence, when I try to build the program, I get messages like

```
undefined reference to `cvLoadImage'
```Any assistance with this problem would be greatly appreciated.

Thanks very much,
Peter Lauren.

---

### Post by crdlb on 2011-11-18
You need to install libcv-dev for the development headers. That will also install the actual library package (libcv2.1) if it isn't   installed already.

If you have those already, what compiler flags are you using?

---


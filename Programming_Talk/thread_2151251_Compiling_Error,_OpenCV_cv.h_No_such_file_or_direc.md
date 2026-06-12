---
title: "Compiling Error, OpenCV: cv.h: No such file or directory"
date: 2013-06-03
forum: Programming Talk
---

### Post by Lieske on 2013-06-03
I'm attempting to complie some code written in c++

```
g++ codename.cpp -o codename
```

However, when I try compiling I get the error:

```
codename.cpp:4:16: fatal error: cv.h: No such file or directory
```

Can someone shed on light on what this error means?

---

### Post by DreeDrunk on 2013-06-04
It seems that the compiler cannot find the header file with the name cv.h called in the fourth line of your code.

---

### Post by steeldriver on 2013-06-04
It's part of the older C API I think - you need libcv-dev as well as libopencv-dev, then you need to give the include path - easiest way is via pkg-config

```
g++ `pkg-config --cflags opencv` codename.cpp -o codename
```

Likewise you will need to tell the linker where to find the actual libs

```
g++ `pkg-config --cflags opencv` codename.cpp `pkg-config --libs opencv` -o codename
```

---


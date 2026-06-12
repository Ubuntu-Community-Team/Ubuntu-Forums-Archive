---
title: "Compiling OpenCV 2.3 on Natty x86-64 bit"
date: 2011-09-13
forum: Packaging and Compiling Programs
---

### Post by fowie on 2011-09-13
I'm trying to compile OpenCV 2.3 on Natty following the [install guide]("http://opencv.willowgarage.com/wiki/InstallGuide").  I'm on x86-64, uname is:
```
2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
I run cmake, and it finished successfully, but it was sticking the -march=i686 line into the C++ flags line.  I finally found that CMakeLists.txt in the OpenCV directory had that tag in it (although it was in a block that it shouldn't have entered if the architecture is x86-64).  I removed the tag so the flags were correct, and it begins to compile, but dies at 8% with the lines:
```

make[2]: *** No rule to make target `/usr/lib/i386-linux-gnu/libz.so', needed by `lib/libopencv_core.so.2.3.0'.  Stop.
make[1]: *** [modules/core/CMakeFiles/opencv_core.dir/all] Error 2

```

I've google everywhere and I can't find anyone installing OpenCV 2.3 on Ubuntu 64-bit.  Does anyone have any experience getting this to work?

---

### Post by fowie on 2011-09-13
Solved my own question.  cmake was not realizing that I was on a 64-bit platform.  I've outlined the full process [here]("http://wiki.fowie.com/?p=10")

---


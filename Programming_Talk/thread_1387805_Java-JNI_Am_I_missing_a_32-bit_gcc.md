---
title: "Java-JNI Am I missing a 32-bit gcc?"
date: 2010-01-22
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2010-01-22
Hello,

Trying to learn JNI. I've got 64-bit Ubuntu and have downloaded and installed **build-essential**, with debug libs. I have googled for hours learning and will comment that the linking that JNI requires is a bit much. Anyway, in the setup for NetBeans tutorial, is a command to limit the C header to **-shared -m32**. When I build the C.h file I get...

```
gcc -shared -m32    -shared -o dist/libJNIDemoCdl.so -fPIC build/Release/GNU-Linux-x86/JNIDemo.o  
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status
make[2]: *** [dist/libJNIDemoCdl.so] Error 1
make[2]: Leaving directory `/home/user/NetBeansProjects/JNIDemoCdl-1'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/user/NetBeansProjects/JNIDemoCdl-1'
make: *** [.build-impl] Error 2
BUILD FAILED (exit value 2, total time: 572ms)
```

Am I missing any 32-bit lib? or any lib32-dev?? Thanks, for any replies, my goal is to JNI OpenCV.

---

### Post by Unterseeboot_234 on 2010-01-22
Excuse, but I found another code recipe online. 

Basically, you build each part of the project you've got going on, then go back to the Java and add a line of code that statically loads your c.header. I don't care about restricting compiled code to 32-bit. I turned off the -shared -m32

I mean from what I can absorb, JNI never was meant to be portable. Too much linking -- almost like spaghetti code.

From here... maybe, just maybe I can get the Ubuntu repository version of OpenCV 1.0 to work with Processing.org OpenCV-(Java).

---


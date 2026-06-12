---
title: "OpenGL and X Window in Netbeans"
date: 2010-09-09
forum: Programming Talk
---

### Post by alatnet on 2010-09-09
Hi, sorta a new programmer to linux and having some problems compiling an opengl project via Netbeans.  I've been able to compile it under windows and is making a version for it under linux but when i run the test program i keep getting a seg fault when the program reaches "XCreateColormap".  I have looked online and cannot find anything on this.  I believe that i have installed all the required development files via KPackage (since im using Kubuntu).  I have no idea why this is happening and i believe that i am compiling the program correctly.

For libraries that im linking i have:
```
Motif (-lXm -lXt -lXext -lX11)
-lGLee (OpenGL Easy Extention library, downloaded binary and linked it from a separate folder)
-lGL
-lGLU
-lfreetype
-lcal3d
-lopenal
Posix Threads (-lpthread)
Data Compression (-lz)
```

This is my library directories that i have the linker search for libraries:
```
/usr/lib
/usr/lib64
/usr/lib/xorg
/lib:/lib64
../../Programming/GLee-5.4.0-src
```

I haven't had that much problems with creating C\C++ applications via Netbeans and it works really well for creating C\C++ apps.
Any help is appreciated!

---

### Post by alatnet on 2010-09-09
Fixed it...
Apparently i was assigning a variable instead of comparing a variable in an if statement...
Thank you Netbeans debug tools!

---


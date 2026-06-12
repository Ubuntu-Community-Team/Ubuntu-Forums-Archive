---
title: "OpenGL + KDevelop + Ubuntu 7.10"
date: 2007-10-20
forum: Programming Talk
---

### Post by malovanyy on 2007-10-20
Hi!
I'm trying to compile program that uses OpenGL in KDevelop. In Project Options -> Configure Options ->C++ -> Compiler Flags I added -lGL -lGLU -lglut. When I'm trying to compile I get an error. That's what is said in  config.log:
```
configure:2609: g++ -O0 -g3 -lGL -lGLU -lglut   conftest.cpp  >&5
/usr/bin/ld: cannot find -lGL
```
Does anyone knows what is the problem?? I used the same method on Mandriva and SLED and it worked fine.

---

### Post by slavik on 2007-10-20
```
sudo apt-get install libgl1-mesa-dev
```

---

### Post by malovanyy on 2007-10-20
P.S. Files /usr/lib/libGL.so.1, libGLU.so.1 and libglut.so.3 are on their places

---

### Post by malovanyy on 2007-10-20
> **slavik said:**
> ```
sudo apt-get install libgl1-mesa-dev
```
Just have installed. Nothing new :(

---

### Post by malovanyy on 2007-10-21
Finally I have solved the problem myself. All I have to do is to make direct symlinks to my GL, GLU and glut library:
```
  
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so
sudo ln -s /usr/lib/libGLU.so.1.3.070001 /usr/lib/libGLU.so
sudo ln -s /usr/lib/libglut.so.3.8.0 /usr/lib/libglut.so
 
```
and install additionl packages because I didn't have GLU and glut headers in /lib/include/GL
```
 sudo apt-get install libglut3 libglut3-dev  libglu1-mesa libglu1-mesa-dev 
```

---


---
title: "where to find OpenGL and OpenCL header files?"
date: 2011-04-13
forum: Packaging and Compiling Programs
---

### Post by ksix on 2011-04-13
Newbie question... 
Trying to port some code to Ubuntu and can't find the <GL/gl.h> and other header files.
They don't seem to exist anywhere on my file system.
Do I need to install something first to get these?   

Using Ubuntu 10.10 with Nvidia 580 graphics card.

Any suggestions?  Thanks!!!

---

### Post by SevenMachines on 2011-04-13
You have at least 2 options as far as i can recall

1. The software opengl headers 
```
 $ sudo apt-get install mesa-common-dev
$ dpkg -L mesa-common-dev |grep gl.h
/usr/include/GL/gl.h
```2. The nvidia opengl headers, i think these are the only ones that have opencl
```
 $ sudo apt-get install nvidia-current-dev
$ dpkg -L nvidia-current-dev | grep gl.h
/usr/include/nvidia-current/GL/gl.h
$ dpkg -L nvidia-current-dev | grep cl.h
/usr/include/nvidia-current/CL/cl.h
```I imagine ati have opencl sdk (stream?) too, but i dont think thats in the repository so you might have to do that manually

nvidia opencl works though, thats what i use

---

### Post by ksix on 2011-04-13
Thank you!  That is very helpful.  Getting closer!
Two follow up newbie questions if you don't mind:

1. "glut.h" does not seem to be included in these, do you know where that one would come from?

2. Do you know the correct way to add these to the include search path, so they are always found by the compiler?

Thanks again!

---

### Post by SevenMachines on 2011-04-14
> **ksix said:**
> 1. "glut.h" does not seem to be included in these, do you know where that one would come from?
```
$ sudo apt-get install freeglut3-dev
```Note, apt-file is quite handy for this sort of thing
```
$ sudo apt-get install apt-file
$ sudo apt-file update
$ apt-file search glut.h
```> 2. Do you know the correct way to add these to the include search path, so they are always found by the compiler?Add them on the command line with -I (capital i) and the libraries with -l, eg
```
$ g++ -o hello hello.cpp -I/usr/include/GL/ -lGL -lglut
```

---

### Post by ksix on 2011-04-14
Thanks!  Getting closer - the compiler finds both gl.h and glut.h fine now.

But unfortunately I still seem to be missing a bunch of GL functions, the compiler gives errors such as:

error: ‘glGenBuffers’ was not declared in this scope
error: ‘glBindBuffer’ was not declared in this scope
error: ‘glBufferData’ was not declared in this scope
error: ‘CGLContextObj’ was not declared in this scope
error: ‘kCGLCPSwapInterval’ was not declared in this scope
error: ‘CGLSetParameter’ was not declared in this scope

This code was developed and works on Mac, but I was hoping it is valid portable GL code...
Do you think I just need to install yet another piece of GL on Ubuntu?
Is there a good place to find which GL functions are available from where?

---

### Post by SevenMachines on 2011-04-14
Try adding -DGL_GLEXT_PROTOTYPES to the compilation line or maybe 
```
#define GL_GLEXT_PROTOTYPES
``` to the source file
Note though, i have a worrying feeling that CGL is an apple specific thing, i dont think the codes portable without replacing those calls, could be wrong (i dont have a mac) but i'm fairly sure

---

### Post by ksix on 2011-04-14
YES!  That did it, thanks a million!

and I think you are right about the CGL being Mac specific.
I removed those for now, and also linked with -lGLU and everything else seems to work!  Woohoo.

---


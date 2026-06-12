---
title: "Plib c++ undefined reference"
date: 2011-05-12
forum: Programming Talk
---

### Post by elguapo159 on 2011-05-12
Hi,

I am new on using ubuntu with g++.  Compiling a "hello world" program  works like a charm. But when I try to compile the simple.cxx from the  plib_examples-1.8.5.tar.gz (src/pui/) with the following command:
g++ -Wall simple.cxx -I /usr/include/ -o simple 
or
g++ simple.cxx -o simple -I/usr/include/plib/

I get:
/tmp/cc8lfK1s.o: In function `motionfn(int, int)':
simple.cxx:(.text+0x14): undefined reference to `puMouse(int, int)'
simple.cxx:(.text+0x19): undefined reference to `glutPostRedisplay'
/tmp/cc8lfK1s.o: In function `mousefn(int, int, int, int)':
simple.cxx:(.text+0x41): undefined reference to `puMouse(int, int, int, int)'
simple.cxx:(.text+0x46): undefined reference to `glutPostRedisplay'
/tmp/cc8lfK1s.o: In function `displayfn()':
simple.cxx:(.text+0x76): undefined reference to `glClearColor'
simple.cxx:(.text+0x82): undefined reference to `glClear'
simple.cxx:(.text+0x87): undefined reference to `puDisplay()'
simple.cxx:(.text+0x8c): undefined reference to `glutSwapBuffers'
simple.cxx:(.text+0x91): undefined reference to `glutPostRedisplay'
/tmp/cc8lfK1s.o: In function `main':
simple.cxx:(.text+0xe0): undefined reference to `glutInitWindowSize'
simple.cxx:(.text+0xf2): undefined reference to `glutInit'
simple.cxx:(.text+0xfe): undefined reference to `glutInitDisplayMode'
simple.cxx:(.text+0x10a): undefined reference to `glutCreateWindow'
simple.cxx:(.text+0x116): undefined reference to `glutDisplayFunc'
simple.cxx:(.text+0x122): undefined reference to `glutMouseFunc'
simple.cxx:(.text+0x12e): undefined reference to `glutMotionFunc'
simple.cxx:(.text+0x1ca): undefined reference to `glutMainLoop'
/tmp/cc8lfK1s.o: In function `puObject::setLegend(char const*)':
simple.cxx:(.text._ZN8puObject9setLegendEPKc[puObject::setLegend(char const*)]+0x25): undefined reference to `puPostRefresh()'
/tmp/cc8lfK1s.o: In function `puButton::puButton(int, int, int, int, int)':
simple.cxx:(.text._ZN8puButtonC2Eiiiii[puButton::puButton(int,  int, int, int, int)]+0x29): undefined reference to  `puObject::puObject(int, int, int, int)'
simple.cxx:(.text._ZN8puButtonC2Eiiiii[puButton::puButton(int,  int, int, int, int)]+0x32): undefined reference to `vtable for  puButton'
/tmp/cc8lfK1s.o: In function `puOneShot::puOneShot(int, int, int, int)':
simple.cxx:(.text._ZN9puOneShotC1Eiiii[puOneShot::puOneShot(int,  int, int, int)]+0x3a): undefined reference to `vtable for puOneShot'
/tmp/cc8lfK1s.o: In function `puGetWindowGLUT()':
simple.cxx:(.text._Z15puGetWindowGLUTv[puGetWindowGLUT()]+0x7): undefined reference to `glutGetWindow'
/tmp/cc8lfK1s.o: In function `puSetWindowGLUT(int)':
simple.cxx:(.text._Z15puSetWindowGLUTi[puSetWindowGLUT(int)]+0xd): undefined reference to `glutSetWindow'
/tmp/cc8lfK1s.o: In function `puGetWindowSizeGLUT(int*, int*)':
simple.cxx:(.text._Z19puGetWindowSizeGLUTPiS_[puGetWindowSizeGLUT(int*, int*)]+0xe): undefined reference to `glutGet'
simple.cxx:(.text._Z19puGetWindowSizeGLUTPiS_[puGetWindowSizeGLUT(int*, int*)]+0x1f): undefined reference to `glutGet'
/tmp/cc8lfK1s.o: In function `puSetWindowSizeGLUT(int, int)':
simple.cxx:(.text._Z19puSetWindowSizeGLUTii[puSetWindowSizeGLUT(int, int)]+0x14): undefined reference to `glutReshapeWindow'
/tmp/cc8lfK1s.o: In function `puInitGLUT()':
simple.cxx:(.text._Z10puInitGLUTv[puInitGLUT()]+0x26):  undefined reference to `puSetWindowFuncs(int (*)(), void (*)(int), void  (*)(int*, int*), void (*)(int, int))'
simple.cxx:(.text._Z10puInitGLUTv[puInitGLUT()]+0x2b): undefined reference to `puRealInit()'
collect2: ld returned 1 exit status

Does someone know what I am doing wrong? I searched the forum but didn't fined a solution for this issue.
It looks like he can't find the correct files but I included the necessary dir.  

I am using ubuntu 10.10 with gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 

Kind regards

---

### Post by MadCow108 on 2011-05-12
you need to link with the libraries defining these symbols.
This should be libplibpu from the libplib-dev package
```

# -l flag adds lib prefix and extension (.so)
g++ simple.cxx -o simple -I/usr/include/plib/ -lplibpu
```
perhaps you also need libglut

---

### Post by elguapo159 on 2011-05-12
Thx for the reply.
I can't get it working like that and I can't seem to find anything in the manpage regarding the -l option.

Executing the code "g++ simple.cxx -o simple -I/usr/include/plib/ -llibpu" gives me the following error:

/usr/bin/ld: cannot find -llibpu
collect2: ld returned 1 exit status

Any ideas?

---

### Post by JupiterV2 on 2011-05-12
> **elguapo159 said:**
> Thx for the reply.
I can't get it working like that and I can't seem to find anything in the manpage regarding the -l option.

Executing the code "g++ simple.cxx -o simple -I/usr/include/plib/ -llibpu" gives me the following error:

/usr/bin/ld: cannot find -llibpu
collect2: ld returned 1 exit status

Any ideas?

Try -lpu. -l is expanded to lib when searching for the library. Therefore, -lmath is expanded to libmath. Therefore -llibpu is expanded to liblibpu, which is not what you want. Alternatively, you may need to run ldconfig or use the -L library path flag to find your library. Something like: -L /usr/lib/plib.

---

### Post by MadCow108 on 2011-05-12
sorry a typo in my first post:
you want -lplibpu
and you need libplib-dev installed

there are two lib in that library
```
apt-file list libplib-dev | grep libpu.so
libplib-dev: /usr/lib/**lib**p**lib**pu.so
```

---

### Post by elguapo159 on 2011-05-12
Thx for the reply. This solved part of my problem.=D>

g++ simple.cxx -o simple -I/usr/include/plib/ -lplibpu

So i still need to solve the following errors:
/tmp/ccHCcImo.o: In function `motionfn(int, int)':
simple.cxx:(.text+0x19): undefined reference to `glutPostRedisplay'
/tmp/ccHCcImo.o: In function `mousefn(int, int, int, int)':
simple.cxx:(.text+0x46): undefined reference to `glutPostRedisplay'
/tmp/ccHCcImo.o: In function `displayfn()':
simple.cxx:(.text+0x8c): undefined reference to `glutSwapBuffers'
simple.cxx:(.text+0x91): undefined reference to `glutPostRedisplay'
/tmp/ccHCcImo.o: In function `main':
simple.cxx:(.text+0xe0): undefined reference to `glutInitWindowSize'
simple.cxx:(.text+0xf2): undefined reference to `glutInit'
simple.cxx:(.text+0xfe): undefined reference to `glutInitDisplayMode'
simple.cxx:(.text+0x10a): undefined reference to `glutCreateWindow'
simple.cxx:(.text+0x116): undefined reference to `glutDisplayFunc'
simple.cxx:(.text+0x122): undefined reference to `glutMouseFunc'
simple.cxx:(.text+0x12e): undefined reference to `glutMotionFunc'
simple.cxx:(.text+0x1ca): undefined reference to `glutMainLoop'
/tmp/ccHCcImo.o: In function `puGetWindowGLUT()':
simple.cxx:(.text._Z15puGetWindowGLUTv[puGetWindowGLUT()]+0x7): undefined reference to `glutGetWindow'
/tmp/ccHCcImo.o: In function `puSetWindowGLUT(int)':
simple.cxx:(.text._Z15puSetWindowGLUTi[puSetWindowGLUT(int)]+0xd): undefined reference to `glutSetWindow'
/tmp/ccHCcImo.o: In function `puGetWindowSizeGLUT(int*, int*)':
simple.cxx:(.text._Z19puGetWindowSizeGLUTPiS_[puGetWindowSizeGLUT(int*, int*)]+0xe): undefined reference to `glutGet'
simple.cxx:(.text._Z19puGetWindowSizeGLUTPiS_[puGetWindowSizeGLUT(int*, int*)]+0x1f): undefined reference to `glutGet'
/tmp/ccHCcImo.o: In function `puSetWindowSizeGLUT(int, int)':
simple.cxx:(.text._Z19puSetWindowSizeGLUTii[puSetWindowSizeGLUT(int, int)]+0x14): undefined reference to `glutReshapeWindow'
collect2: ld returned 1 exit status

Should i do the same thing for the glut errors? I installed  libglut3-dev for this.

Thx

---

### Post by MadCow108 on 2011-05-12
yes -lglut this time

you can check symbols of libraries with the *nm* tool
```
$ nm --dynamic /usr/lib/libglut.so | grep glutInitWindowSize
000000000001e630 T glutInitWindowSize
```
have a look at the manpage for details

---

### Post by elguapo159 on 2011-05-13
Thx man. Your last reply solved the problem.
Thx for al the help.

Final command was:
g++ simple.cxx -o simple -I/usr/include/plib/ -lplibpu -lglut

---


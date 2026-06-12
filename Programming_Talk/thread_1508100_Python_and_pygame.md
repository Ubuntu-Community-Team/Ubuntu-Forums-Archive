---
title: "Python and pygame"
date: 2010-06-12
forum: Programming Talk
---

### Post by Atzu on 2010-06-12
Hi, I need help with python and pygame... I'm supposed to do a chess in python 3.1 and decided to use pygame... I installed it (synaptics) and tried to import it... but when I try to import it I get this error message:

```
Traceback (most recent call last):
  File "<pyshell#5>", line 1, in <module>
    import pygame
ImportError: No module named pygame
```

I'm using pygame 1.9.1. Anyone know how to import it correctly? or how to install it so that I can use it on python 3.1?

I'd use python 2.6 but our teacher told us to use 3.1 :/ help me please!!

Thanks.

---

### Post by DanielWaterworth on 2010-06-12
The repo package doesn't have the python3 module, I had the same problem. I solved it by compiling pygame from source. I think I downloaded it and untared it, then:

$ python3 config.py
$ 2to3 setup.py -w
$ sudo python3 setup.py

You'll need to do this to each computer that you'll use your game on unless you put pygame into a local folder. If you have any problems, just post them back here.

---

### Post by Atzu on 2010-06-12
Thanks a lot! ^^ but... everything went fine until i run the last command (sudo python3 setup.py)... here's what i get:

```

No Arguments Given, Perform Default Install? [Y/n]y
Skipping module _numericsurfarray for Python 3.1.1+ (r311:74480, Nov  2 2009, 14:49:22) 
[GCC 4.4.1] build.
Skipping module _numericsndarray for Python 3.1.1+ (r311:74480, Nov  2 2009, 14:49:22) 
[GCC 4.4.1] build.
Skipping module scrap for Python 3.1.1+ (r311:74480, Nov  2 2009, 14:49:22) 
[GCC 4.4.1] build.
Skipping module _camera for Python 3.1.1+ (r311:74480, Nov  2 2009, 14:49:22) 
[GCC 4.4.1] build.
running install
running build
running build_py
running build_ext
building 'pygame.imageext' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -D_REENTRANT -I/usr/X11R6/include -I/usr/include/SDL -I/usr/include/SDL -I/usr/include -I/usr/include -I/usr/include/python3.1 -c src/imageext.c -o build/temp.linux-i686-3.1/src/imageext.o
In file included from src/imageext.c:47:
src/pygame.h:75:20: error: Python.h: No such file or directory
In file included from src/imageext.c:47:
src/pygame.h:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lenfunc’
src/pygame.h:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizeargfunc’
src/pygame.h:124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizeobjargproc’
src/pygame.h:125: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizessizeargfunc’
src/pygame.h:126: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizessizeobjargproc’
src/pygame.h:127: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘readbufferproc’
src/pygame.h:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘writebufferproc’
src/pygame.h:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘segcountproc’
src/pygame.h:130: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘charbufferproc’
src/pygame.h:234: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:275: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:310: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:349: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:387: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:450: error: expected specifier-qualifier-list before ‘PyObject’
src/pygame.h:457: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:499: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:567: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/imageext.c:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/imageext.c: In function ‘opengltosdl’:
src/imageext.c:506: warning: implicit declaration of function ‘PyErr_SetString’
src/imageext.c:506: error: ‘PyExc_RuntimeError’ undeclared (first use in this function)
src/imageext.c:506: error: (Each undeclared identifier is reported only once
src/imageext.c:506: error: for each function it appears in.)
src/imageext.c:506: error: ‘PyObject’ undeclared (first use in this function)
src/imageext.c:506: error: expected expression before ‘)’ token
src/imageext.c:510: error: expected expression before ‘)’ token
src/imageext.c:517: error: ‘PyExc_MemoryError’ undeclared (first use in this function)
src/imageext.c:517: error: expected expression before ‘)’ token
src/imageext.c:537: error: expected expression before ‘)’ token
src/imageext.c:537: error: expected expression before ‘)’ token
src/imageext.c: At top level:
src/imageext.c:552: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/imageext.c:646: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_imageext_methods’
src/imageext.c:657: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘initimageext’
error: command 'gcc' failed with exit status 1

```

Any idea?

---

### Post by DanielWaterworth on 2010-06-12
sudo apt-get install python3-dev is the command your looking for.

---

### Post by Atzu on 2010-06-12
Thanks! It works great now :)

---

### Post by Ildanach on 2010-06-22
I have this exact same problem. However, your steps didn't work for me. It seems to have installed correctly, but i still can't get it to import into idle.

---

### Post by Atzu on 2010-06-23
You are not getting any error message?

---

### Post by Ildanach on 2010-06-25
Well, it doesn't seem to like it when i use the command python3, so i just used plain python, and it seemed to compile perfectly. It just doesn't show up in idle.

---

### Post by DanielWaterworth on 2010-06-26
python2 modules don't work in python3 and vice versa. Is Idle for python 2 or 3?

---

### Post by zengrz on 2010-06-27
Thx so much u saved my life!

---

### Post by Tony Flury on 2010-06-28
zengrz : I do hope you are exagerating - if not - and you really are developing life critical applications in python then I am worried :-)

---

### Post by DanielWaterworth on 2010-06-28
> **Tony Flury said:**
> zengrz : I do hope you are exagerating - if not - and you really are developing life critical applications in python then I am worried :-)

Nothing like developing life critical applications to wake you up in the morning [=

---

### Post by Ildanach on 2010-06-28
Its for python 3.1.

---

### Post by ctdragon on 2011-10-08
I hate to re-open an old thread, but I had the hardest time installing pygame with a version of python that was not Ubuntu's default build. So I created this tutorial/ how to:

[Install python3.1 and pygame1.9.1 in Ubuntu]("https://sites.google.com/site/cslappe1/knowledge-base-and-how-to-s/installpython31andpygame191inubuntu"):

[https://sites.google.com/site/cslappe1/knowledge-base-and-how-to-s/installpython31andpygame191inubuntu](https://sites.google.com/site/cslappe1/knowledge-base-and-how-to-s/installpython31andpygame191inubuntu)

I hopes this helps the next unfortunate soul to try this.

---


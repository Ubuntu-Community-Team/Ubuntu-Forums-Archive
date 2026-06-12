---
title: "New to programming on Ubuntu"
date: 2013-06-03
forum: Programming Talk
---

### Post by schievelbein on 2013-06-03
I am an old timer with programming but have not done anything in years and years.
I wanted to start it back up with C++ and OpenGl on Ubuntu.
I have GCC and OpenGL installed and running as far as I know.
When I run the tutorials from [http://openglbook.com/](http://openglbook.com/), I can get past the first 3 chapters and run the tutorials.
The output from Chapter1 shows:      INFO: OpenGL Version 4.0.0 NVIDIA 319.23
All of Chapter 1,2,&3 run fine.
When I try to compile Chapter4 with "gcc -I/usr/include -L/usr/lib -lglut -lGL -lGLU -lGLEW Chapter4.c"
I get the following errors:
/tmp/cce06EGv.o:Chapter4.c:function Initialize: error: undefined reference to 'ExitOnGLError'
/tmp/cce06EGv.o:Chapter4.c:function Initialize: error: undefined reference to 'ExitOnGLError'
/tmp/cce06EGv.o:Chapter4.c:function Initialize: error: undefined reference to 'TranslateMatrix'
/tmp/cce06EGv.o:Chapter4.c:function ResizeFunction: error: undefined reference to 'CreateProjectionMatrix'
/tmp/cce06EGv.o:Chapter4.c:function CreateCube: error: undefined reference to 'ExitOnGLError'
/tmp/cce06EGv.o:Chapter4.c:function CreateCube: error: undefined reference to 'LoadShader'
/tmp/cce06EGv.o:Chapter4.c:function CreateCube: error: undefined reference to 'LoadShader'
/tmp/cce06EGv.o:Chapter4.c:function CreateCube: error: undefined reference to 'ExitOnGLError'
/tmp/cce06EGv.o:Chapter4.c:function DrawCube: error: undefined reference to 'DegreesToRadians'
/tmp/cce06EGv.o:Chapter4.c:function DrawCube: error: undefined reference to 'RotateAboutY'
/tmp/cce06EGv.o:Chapter4.c:function DrawCube: error: undefined reference to 'RotateAboutX'

I have copied the Utils.* and Simple*.* files to the same directory.
I do not know if they need special permissions or what.
I would appreciate any ideas of suggestions.
I usually use Geany, but tried with commandline and received the same results.

How go I check and make sure my OpenGL and FreeGlut are installed correctly?

THANKS
Michael

---

### Post by dwhitney67 on 2013-06-03
List your source files before listing the libraries it depends on.  For example:
```

gcc -I/some/include/path MySource.c -L/some/lib/path -lsomelib

```

---


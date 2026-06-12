---
title: "OpenGL general question"
date: 2011-12-17
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2011-12-17
Hello

I would like to start learning OpenGL however I don't know where to start, it is so confusing.:confused: 
In fact I am not quite sure how it works and I wasn't able to find any relevant informations.

What is OpenGL? How it is implemented? how can I include OpenGL into my project?

I find something called freeglut which seems to be an implementation of OpenGL, but it really confuse me, because there is OpenGL version 2,3 and 4 and freeglut comes in 2.6(stable) and 2.8(development), but what OpenGL it use? How can I write only with OpenGL 2 or 3? What is GLU? 
Another think that I don't understand is, that when graphic card support OpenGL 3 will it be able to run OpenGL 4 applications?

also how do you know what version of OpenGL do your graphic card support?

What is MESA?

Last question what is the relation between graphic card, X server, OpenGL, freeglut, MESA and GLU?

Totally confused :(

---

### Post by satsujinka on 2011-12-17
OpenGL is a specification for the functionality that a library (such as freeglut) to support. Most graphics cards include features to make this easy and any recent card probably supports version 4 of the spec. However, most implementations of OpenGL are only at version 2 of the spec. with a few of the version 3 features also implemented.

If I remember correctly X does not use OpenGL. MESA is an implementation of the OpenGL spec. GLU is simply a library that implements higher order functions based on openGL, it is related to GLUT and freeglut in that they also provide libraries for working with OpenGL.

As to your question about running OpenGL 4 apps, only a gpu that supports version 4 can run code for version 4. However, detecting what is supported and working around the limitations of a card can be done, and probably is done by the library (you'll need to look that up though.)

If you want more info, you should take a look at the OpenGL wikibook.

---

### Post by t1497f35 on 2011-12-17
For you to use a given version of OpenGL both your video card and your driver must support it, often you have several OpenGL drivers installed on your computer and you must know which driver is currently in use. For example, Intel users only have 1 driver, but Nvidia users can have both the open source "nouveau" driver and the proprietary Nvidia driver (the latter is the best one) installed on their computers.

To use OpenGL in your app you have to do a lot of housekeeping, like creating a window, an OpenGL context and other fancy stuff - that's why freeglut exists, it can easily help you create all of that in a few simple steps.

OpenGL means both the OpenGL standard and the library in your computer and you have to figure out for yourself from context when OpenGL is meant as "graphics standard" and when it's meant as "the libraries/files from your computer implementing OpenGL". Just like Java is a brand, a technology, a language, a runtime and you figure out from the context what the author means by saying "Java".


You have to read quite a lot of non-OpenGL info for you to understand how to program with OpenGL, but the easiest way to get started and using OpenGL is searching for a freeglut (glut) tutorial.

To install freeglut on Ubuntu: sudo apt-get install freeglut3-dev

---

### Post by Mr.Pytagoras on 2011-12-17
Thanks It's much clearer now. But just to be sure

I have googled a bit and also did a little finding on my computer and I have found that I have in /usr/include/GL this

```

-rw-r--r-- 1 root root   7830 2011-01-19 05:35 freeglut_ext.h
-rw-r--r-- 1 root root    681 2011-01-19 05:35 freeglut.h
-rw-r--r-- 1 root root  26152 2011-01-19 05:35 freeglut_std.h
-rw-r--r-- 1 root root 680842 2011-02-03 18:25 glew.h
-rw-r--r-- 1 root root 634365 2011-08-23 00:38 glext.h
-rw-r--r-- 1 root root  84670 2011-08-23 00:38 gl.h
-rw-r--r-- 1 root root 128943 2011-08-23 00:38 gl_mangle.h
-rw-r--r-- 1 root root  17251 2011-08-23 00:38 glu.h
-rw-r--r-- 1 root root   3315 2011-08-23 00:38 glu_mangle.h
-rw-r--r-- 1 root root    639 2011-01-19 05:35 glut.h
-rw-r--r-- 1 root root  57202 2011-02-03 18:25 glxew.h
-rw-r--r-- 1 root root  43887 2011-08-23 00:38 glxext.h
-rw-r--r-- 1 root root  17170 2011-08-23 00:38 glx.h
-rw-r--r-- 1 root root   3463 2011-08-23 00:38 glx_mangle.h
drwxr-xr-x 2 root root   4096 2011-12-17 20:34 internal
-rw-r--r-- 1 root root  53806 2011-02-03 18:25 wglew.h

```So if I understand it correctly(correct my if I'wrong) 
The  gl.h is the OpenGL header (library in my computer) which contain list  of OpenGL functions, defines, types ... if I include this header into my  program and call for example
```

void glShadeModel( GLenum mode );

```It  will execute the implementation of that function from the MESA library  and MESA will call the driver which will do some magic with the graphic  card and I will see the result on my screen. ??? 

The freeglut's  function is something like a collection of functions from the gl.h  header plus some signals and events handling, windowing ...?

Do I understand it correctly?

Also:
```

supercomp:/usr/include/GL$ glxinfo
direct rendering: Yes
...
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
...

```This  means that my OpenGL is at version 2.1? and that direct rendering means  that the OpenGL calls will be processed on the GPU not emulated on CPU?

What is the GLX version?

PS:
Thanks you for those answers

---

### Post by t1497f35 on 2011-12-18
Yes, gl.h is the header, the library itself is in /usr/lib, usually called "libGL.so" which is usually a link to a real library or to another link which in the end leads to the final (real) library.
For example, on my computer if I call "ls /usr/lib | grep GL"
it gives me:
```

libGLEW.a
libGLEWmx.so.1.5
libGLEWmx.so.1.5.2
libGLEW.so
libGLEW.so.1.5
libGLEW.so.1.5.2
libGL.la
libGL.so
libGL.so.1
libGL.so.290.10

```where libGL.so is the OpenGL library but it's really a link to libGL.so.1 which is a link to the actual (real) OpenGL library libGL.so.290.10 - that's because my nvidia driver version is 290.10, and that's how nvidia manages its libraries.

> It  will execute the implementation of that function from the MESA  library  and MESA will call the driver which will do some magic with the  graphic  card and I will see the result on my screen. ??? Yeah

> 
This  means that my OpenGL is at version 2.1? and that direct rendering  means  that the OpenGL calls will be processed on the GPU not emulated  on CPU?
Mostly yes. You see, sometimes even if it's advertised with "direct rendering: yes", some functions might be implemented on the CPU rather than the GPU for different reasons: the library creator didn't have time/knowledge to implement it in hardware or because your graphics card isn't capable of executing a particular OpenGL call so it had to be emulated on the CPU for your OpenGL library to be fully compatible with OpenGL 2.1.

[GLX]("http://en.wikipedia.org/wiki/GLX") is the mechanism which allows OpenGL to run on systems using the X server (all UNIXes and Linux), on Windows it's called GLW (cause OpenGL runs on Windows). That's because OpenGL needs to hook into the OS to be able to configure itself & run.

There's also [EGL]("http://en.wikipedia.org/wiki/EGL_%28OpenGL%29") but don't pay attention to these EGL/GLX/GLW cause they're likely to confuse you. Just work with freeglut which hides a lot of complexity from you. Remember, OpenGL isn't for novices and you'll have to read a lot and be patient.

---

### Post by Mr.Pytagoras on 2011-12-18
I think that I understand it now. Thanks

However I still have a question ;)

I have an Intel HD graphics 3000 which according to wikipedia(coudn't find relevant info on intel's pages) has support for OpenGL 3.1 but my computer seems to work only with OpenGL 2.1 is this because Intel doesn't provide their own implementation of OpenGL, but uses MESA?

I have also read that NVIDIA provide their own implementation of OpenGL, why not also intel?

Do i have an option with intel graphics? can I use different OpenGL implementations with intel graphics card? or do I have to wait for MESA to support OpenGL 3?(which from what I have read is planned in version 7.12/8. Not that I'm too impatient but I would like to know what are my choices)

---

### Post by t1497f35 on 2011-12-19
Intel does provide its own implementation - it is integrated into Mesa, so you're actually using Intel's driver, which is open source, unlike the AMD and Nvidia users who have both an open source and a closed source driver each. There's an exception - the Intel GMA series hw which is a different story, but there's few such hw on the market.

Starting with last year Intel improved its OpenGL 2D/3D drivers a lot (and also its commitment to graphics drivers on Linux), if 2 years ago all Intel drivers were pure crap - nowadays you can even play most 3D games without glitches and some of them at a decent framerate.

Currently OpenGL 3.0+ isn't supported by **any** open source graphics drivers, but Intel is set to deliver the first open source OpenGL 3.0 compatible driver if not by years end - then in January-February 2012 for sure, which as you know will be part of Mesa 7.12/8.0, which will ship with Ubuntu 12.04, so, with some luck, you could have OpenGL 3.0+ next year.

Besides OpenGL there's also video playback acceleration which should be implemented in hw, the best solutions on Linux are VA-API and VDPAU. The latest versions of Flash use so far only VDPAU to accelerate video playback (h264), which is only supported by the closed source Nvidia driver. The intel driver (so far) supports VA-API.

The short story with the other vendors is:
AMD - provides both open and closed source drivers (the closed source driver is fully developed by AMD, and the open source one - mostly  by AMD).
Nvidia - provides only closed source drivers, but there's the "nouveau" open source nvidia driver which is being developed by programmers from Red Hat and other places. An employee from Nvidia Corporation said the company won't help nor impede the development of this open source driver.

---

### Post by Mr.Pytagoras on 2011-12-19
So I'm using Intel's implementation actually.

It's much clearer after this thread to me.

Thanks you.

---


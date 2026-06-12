---
title: "[SOLVED] Getting started with openGL"
date: 2008-09-12
forum: Programming Talk
---

### Post by Yuki_Nagato on 2008-09-12
I need to learn to program basic openGL applications and such.  The problem is, any online tutorials I find just get to programming, and do not deal with initial setup.

I believe I need those header files (glx.h, gl.h, glu.h) in order to compile the C and C++ programs I am writing.  Shouldn't they already be installed?

I installed "build-essential" and have compiled and run C and C++ programs.  It is just that the compiler spits back "not found" errors for the "GL_***" functions.

---

### Post by rnodal on 2008-09-12
Here is my humble recommendation. I would suggest for you to install either something like a perl, pythong binding to OpenGL(I'm not sure if this is the right terminology) or install [SDL]("www.libsdl.org") or [GLFW]("glfw.sourceforge.net"). These libraries will handle the boring stuff for you. Creating a window, handling input etc. Believe me you do not want to code what those libraries do from scratch :).

 > The problem is, any online tutorials I find just get to programming, and do not deal with initial setup.

What do you mean? Not matter which way you go you need to "program". Unless you use some sort of tool that will do things for you but I think you want to learn. Once you have managed to create a window with SDL or GLFW all you have to do is to follow any OpenGL tutorial like NeHe collections etc.

-r

---

### Post by techmarks on 2008-09-12
> **Yuki_Nagato said:**
> I need to learn to program basic openGL applications and such.  The problem is, any online tutorials I find just get to programming, and do not deal with initial setup.


I suspect there's a need for a information reference like this , just a simple GL setup with a basic window displaying some shape for the different toolkits. (wxwidgets, GTK+, etc...)

I looked at the recommendation of  GLFW but it seems limited;

> 
   It allows you to create an OpenGL-capable window. No menus, no buttons.
   
   



Seems all it does is put up a window that you can render into.



You might be better off just using GTK+ or QT, even FLTK is a good choice, it's the one I'm using right now for the function graphing program I'm working on.
 
It's super simple to set up OpenGL with FLTK, and GTK+ is not so bad with GTK you'll also need the gtkglext library.

If you need a GUI with OpenGL capability GLFW doesn't seem like what you need.

What exactly are you wanting to do?


> **Yuki_Nagato said:**
> I installed "build-essential" and have compiled and run C and C++ programs. It is just that the compiler spits back "not found" errors for the "GL_***" functions.

Before dealing with this, we'd still need to know how you are going to create your OpenGL window?

OpenGL does not create a window for you to render into. You could even create your window with Xlib , but the point is you'll need to sort that out first.

---

### Post by rnodal on 2008-09-12
> **techmarks said:**
> 
I looked at the recommendation of  GLFW but it seems limited;
Seems all it does is put up a window that you can render into.


It does more than just put up a window :). The op seems to want to learn OpenGL and not a GUI tool kit. Also, he needs to learn how to help the compiler find the needed libraries and headers. 

-r

---

### Post by PeterBBB on 2008-09-12
> I need those header files (glx.h, gl.h, glu.h) in order to compile the C and C++ programs I am writing

Search in Synaptic for a package with glx & dev in the name, Description will be someting like "driver development files"

For example, my driver is nvidia-glx-new-envy, and the matching package nvidia-glx-new-dev-envy contains a glx.h & gl.h

Also, see
_[http://ubuntuforums.org/showpost.php?p=2365634&postcount=2](http://ubuntuforums.org/showpost.php?p=2365634&postcount=2)_

---

### Post by bfhicks on 2008-09-12
[glutmaster]("http://www.stetten.com/george/glutmaster/glutmaster.html") is what I would suggest for just starting out. It sets up a demoWindow class that you can use. It's fairly simple and uses C++ wrappers for the callback functions. All you have to do is make sure 'glut' is installed (search synaptic) and then download all the files into a directory. Then, you'll just have to do a 'make' and you should have a running application with two shapes. Super easy to modify and do your own stuff, just have to touch two methods.

---

### Post by cb951303 on 2008-09-12
> **Yuki_Nagato said:**
> I need to learn to program basic openGL applications and such.  The problem is, any online tutorials I find just get to programming, and do not deal with initial setup.

I believe I need those header files (glx.h, gl.h, glu.h) in order to compile the C and C++ programs I am writing.  Shouldn't they already be installed?

I installed "build-essential" and have compiled and run C and C++ programs.  It is just that the compiler spits back "not found" errors for the "GL_***" functions.

okay first you need to install these
```

sudo apt-get install mesa-common-dev libgl1-mesa-dev libglu1-mesa-dev

```

than you can include opengl headers like this
```

#include <GL/gl.h>
#include <GL/glu.h>
...

```

to compile your project add these as linker flags
```

-lGL -lGLU

```

thats all you need to get started, also I highly recommend that you use glfw, glut or sdl. glfw is the simplest among these but it's very powerful too. also look at [nehe.gamedev.net]("http://nehe.gamedev.net") for tutorials :popcorn:

---

### Post by Yuki_Nagato on 2008-09-12
Thank you all.

I am beginning to receive less errors than before.  Which libraries I had to install was most useful.  I will continue to pursue this.

---

### Post by Yuki_Nagato on 2008-09-13
[PHP]/tmp/cc97Lses.o: In function `resize':
open_GL.c:(.text+0x16b): undefined reference to `glutPostRedisplay'
/tmp/cc97Lses.o: In function `display':
open_GL.c:(.text+0x5d1): undefined reference to `glutSwapBuffers'
/tmp/cc97Lses.o: In function `main':
open_GL.c:(.text+0x5f7): undefined reference to `glutInit'
open_GL.c:(.text+0x603): undefined reference to `glutInitDisplayMode'
open_GL.c:(.text+0x61a): undefined reference to `glutInitWindowSize'
open_GL.c:(.text+0x62e): undefined reference to `glutInitWindowPosition'
open_GL.c:(.text+0x63a): undefined reference to `glutCreateWindow'
open_GL.c:(.text+0x646): undefined reference to `glutDisplayFunc'
open_GL.c:(.text+0x652): undefined reference to `glutIdleFunc'
open_GL.c:(.text+0x65e): undefined reference to `glutReshapeFunc'
open_GL.c:(.text+0x66a): undefined reference to `glutKeyboardFunc'
open_GL.c:(.text+0x676): undefined reference to `glutSpecialFunc'
open_GL.c:(.text+0x680): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status
[/PHP]

That is what I get when I link up with:

```
gcc -lGL -lGLU open_GL.c

```

Does anyone recognize what functions those are from?  I ran some through Google, and the Windows people are linking up "glut32" and other "*32" files.

I am using GLUT in this code.

Such junk as:
```

gcc file.c -lglut -lGL -lGLU -lX11 -lXmu

```

does not work.

---

### Post by WitchCraft on 2008-09-13
> **Yuki_Nagato said:**
> [PHP]/tmp/cc97Lses.o: In function `resize':
open_GL.c:(.text+0x16b): undefined reference to `glutPostRedisplay'
/tmp/cc97Lses.o: In function `display':
open_GL.c:(.text+0x5d1): undefined reference to `glutSwapBuffers'
/tmp/cc97Lses.o: In function `main':
open_GL.c:(.text+0x5f7): undefined reference to `glutInit'
open_GL.c:(.text+0x603): undefined reference to `glutInitDisplayMode'
open_GL.c:(.text+0x61a): undefined reference to `glutInitWindowSize'
open_GL.c:(.text+0x62e): undefined reference to `glutInitWindowPosition'
open_GL.c:(.text+0x63a): undefined reference to `glutCreateWindow'
open_GL.c:(.text+0x646): undefined reference to `glutDisplayFunc'
open_GL.c:(.text+0x652): undefined reference to `glutIdleFunc'
open_GL.c:(.text+0x65e): undefined reference to `glutReshapeFunc'
open_GL.c:(.text+0x66a): undefined reference to `glutKeyboardFunc'
open_GL.c:(.text+0x676): undefined reference to `glutSpecialFunc'
open_GL.c:(.text+0x680): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status
[/PHP]

That is what I get when I link up with:

```
gcc -lGL -lGLU open_GL.c

```

Does anyone recognize what functions those are from?  I ran some through Google, and the Windows people are linking up "glut32" and other "*32" files.

I am using GLUT in this code.

Such junk as:
```

gcc file.c -lglut -lGL -lGLU -lX11 -lXmu

```

does not work.

apt-get update
apt-cache search glut

apt-get install apt-file
apt-file update
apt-file search glu.h
> 
all:~# apt-file search glut.h
autoconf-archive: /usr/share/doc/autoconf-archive/html/ax_check_glut.html
doc-linux-html: /usr/share/doc/HOWTO/en-html/Nvidia-OpenGL-Configuration/instglut.html
fltk1.1-doc: /usr/share/doc/fltk1.1-doc/HTML/glut.html
freeglut3-dev: /usr/include/GL/freeglut.h
freeglut3-dev: /usr/include/GL/glut.h
freeglut3-dev: /usr/share/doc/freeglut3-dev/freeglut.html
libguichan-dev: /usr/include/guichan/glut.hpp
libroot5.18: /usr/lib/root/5.18/cint/include/GL/glut.h
python-opengl-doc: /usr/share/doc/python-opengl-doc/documentation/pydoc/OpenGL.GLUT.freeglut.html
python-opengl-doc: /usr/share/doc/python-opengl-doc/documentation/pydoc/OpenGL.tests.test_loadglut.html


> 
all:~# apt-file search glu.h
autoconf-archive: /usr/share/doc/autoconf-archive/html/ax_check_glu.html
gambas2-doc: /usr/share/gambas2/help/help/comp/gb+opengl/glu.html
libfltk1.1-dev: /usr/include/FL/glu.h
libglu1-mesa-dev: /usr/include/GL/glu.h
libroot5.18: /usr/lib/root/5.18/cint/include/GL/glu.h
libsdl-erlang: /usr/lib/erlang/lib/esdl-0.96.0626/c_src/esdl_glu.h
libsdl-erlang: /usr/lib/erlang/lib/esdl-0.96.0626/include/glu.hrl
libsdl-erlang: /usr/share/doc/libsdl-erlang/html/doc/glu.html
mingw32-runtime: /usr/i586-mingw32msvc/include/GL/glu.h


sudo apt-get install freeglut3 freeglut3-dbg freeglut3-dev libglu1-mesa libglu1-mesa-dev libglui2c2 libglui-dev libglut3 libglut3-dev

gcc OpenGL.c -o test -lglut

---

### Post by cb951303 on 2008-09-13
> **Yuki_Nagato said:**
> 

Such junk as:
```

gcc file.c -lglut -lGL -lGLU -lX11 -lXmu

```

does not work.

because you need to install glut libraries from repo

---

### Post by Yuki_Nagato on 2008-09-13
WitchCraft, your step-by-step, all-inclusive, every-command-needed tutorial turned the trick.

Thank you very much.

The "apt-file" commands could not find the python based glut.h files (most likely stems from the fact that I am running Elyssa), but your laundry list of library files to include in apt-get solved my problems.  Telling me what to link also helped.

---

### Post by skullmunky on 2008-09-14
btw you could also check out OpenFrameworks (openframeworks.cc) which is a GLUT-based framework for opengl and lots of other fun stuff.  i think they're sort of osx-centric but the linux version should be good too.

---

### Post by QIII on 2013-02-19
This is a very, very old thread.  You would get as much better response starting a new thread of your own.

Feel free to link this thread in a new one you start.

Best wishes.

Thread closed.

---


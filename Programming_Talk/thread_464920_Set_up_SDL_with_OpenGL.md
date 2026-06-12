---
title: "Set up SDL with OpenGL"
date: 2007-06-05
forum: Programming Talk
---

### Post by PureW on 2007-06-05
**EDIT: The problem is that SDL can't find GL/glu.h.**

Hello, I need help setting up SDL and OpenGL in Ubuntu 7.04 64bits.
I installed my nvidia drivers from nvidia.com.
This far I have only programmed in Windows and Visual Studio 
but now I need help getting started in Ubuntu. I don't know what packages
and editors I need, although I've heard Emacs and Vim are the best.

But that's not the main issue. After following [http://www.libsdl.org/faq.php?action=listentries&category=3#21](http://www.libsdl.org/faq.php?action=listentries&category=3#21)
and doing:
```
g++ -o Test sdltest.cpp `sdl-config --cflags --libs`
```

EDIT: I did 
grep file | g++ -o Test sdltest.cpp `sdl-config --cflags --libs`
and then it said:
/usr/local/include/SDL/SDL_opengl.h:45:58:** error: GL/glu.h: No such file or directory**

From another thread I found out I had to install ibgl1-mesa-dev but that did not help.

sdltest.cpp looks like this: 
```
#include <iostream>
#include <SDL_opengl.h>

int main() {

  std::cout << "Hello world!\n";

  return 1;
}

```I compiled SDL from source with 
./configure
make
sudo make install

And I read and followed this: [http://www.libsdl.org/faq.php?action=listentries&category=3#23](http://www.libsdl.org/faq.php?action=listentries&category=3#23)
and now my  /etc/ld.so.conf contains:
```
include /etc/ld.so.conf.d/*.conf
include /usr/local/lib
``` I think it looks like Im missing some header-files but I don't know which ones.
I have tried googling but with no good results.

---

### Post by Mickeysofine1972 on 2007-06-05
Hi have you tried the HOWTO on the Ubuntu Game Developers Wiki?

[http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com)

Mike

---

### Post by PureW on 2007-06-05
> **Mickeysofine1972 said:**
> Hi have you tried the HOWTO on the Ubuntu Game Developers Wiki?

[http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com)

Mike

Aye, but that didn't help much. I apt-getted:
mesa-common-dev
libglu1-mesa-dev
but I already had those.

---

### Post by WW on 2007-06-05
What is the output of this command?
```

$ sdl-config --cflags

```

---

### Post by PureW on 2007-06-05
```
$ sdl-config --cflags
-I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT

```

---

### Post by WW on 2007-06-05
OK, no surprise there--it is correctly using the files that you installed in /usr/local.

Strange.  The file SDL_opengl.h has these lines:
```

#include <GL/gl.h>	/* Header File For The OpenGL Library */
#include <GL/glu.h>	/* Header File For The GLU Library */

```
Your error message says that when the compiler is processing SDL_opengl.h, it can't find GL/glu.h, which really means it can't find /usr/include/GL/glu.h.  In 7.04, this header is provided by the package libglu1-mesa-dev, which you say you have installed.  Does the file /usr/include/GL/glu.h actually exist?

Are header files and libraries organized any differently for 64 bit versions?

(This is no probably no help, but for what it's worth:  I am running Dapper on a 32 bit computer with SDL installed from the repositories, and your test program compiled fine.)

---

### Post by PureW on 2007-06-05
Yes, the gl.h, glu.h etc, exists in /usr/include/GL/

I wonder if it could have anything to do with my video card drivers?
They did give me headache when trying to install them. But now I
have drivers from nvidia's site. 
$ glxinfo | grep render says this:
```
$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce 6800 LE/AGP/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
```
So I guess I have working drivers, right?

---

### Post by PureW on 2007-06-05
I tried to compile something called SDLGears-1.0.2 and configure went oke,
but when I entered make, it just said :
```
$ make
gcc -DPACKAGE=\"SDLgears\" -DVERSION=\"1.0.2\"  -I. -I.      -g -O2 -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -c gears.c
gears.c:39:21: **error: GL/glut.h: No such file or directory**
```
followed by alot of errors caused by undefined stuff.

I've been trying to get this to work all day, it's really annoying :(

---

### Post by PureW on 2007-06-05
After rebooting the whole computer instead of just restaring X it works....

Annoying it is.

---

### Post by Mickeysofine1972 on 2007-06-06
Learned much you have ;-D

Yoda

---

### Post by paultag on 2008-10-24
For Posterity,

Just ran into an issue with similar symptoms.

The library flags in the Makefile or passed in _have_ to be upper case, if you are making the Makefile by hand or using G++ from the CLI.

-lSDL versus -lsdl.

Cheers,
Tag

---


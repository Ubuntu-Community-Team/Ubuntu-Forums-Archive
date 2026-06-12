---
title: "What should i install for C++/opengl programming"
date: 2007-01-08
forum: Programming Talk
---

### Post by wannaBeHacker on 2007-01-08
Hey can someone please tell me what  packages i need to install to be able to program in c++ and in opengl.

i used to use eclipse.

And i want to do this all through the terminal, so please help me to do this through the terminal thank you!

---

### Post by tzulberti on 2007-01-08
For C++ programming you should install:
build-essential
manpages-dev (man pages about C++)

---

### Post by hod139 on 2007-01-08
For OpenGL you want libgl1-mesa-dev and you probably also want libglu1-mesa-dev (for the glu* commands).

---

### Post by wannaBeHacker on 2007-01-08
thanks, but im really a super noob

how do i install the packages again?

sudo apt-get build-essential?

---

### Post by dlai on 2007-01-08
sudo apt-get install <package-name>

You can also use synaptic, which is the graphical interface for installing packages... It is in System->Administration->Synaptic Package Manager, if you are using Ubuntu. If you are using Kubuntu use Adept, I think it is in System Services (or something like that),

If you need any other help just say so... I've been doing quite a lot of SDL/OpenGL programming in ubuntu.

---

### Post by Wybiral on 2007-01-08
You will probably want to install SDL, it's a library that offers things like initializing the window, catching events (mouse/keyboard/window close) and some other stuff. It will be under libsdl in synaptic, I think you need "libsdl1.2debian" and "libsdl1.2-dev" you may also want "libsdl-image1.2-dev" which is a library that makes loading textures a LOT easier.

Another option, as opposed to SDL, is GLUT. It's a little more restrictive than SDL, but it's smaller and most people find it easier to use. I believe the packages are "freeglut3" and "freeglut3-dev"

These are things you'll need to install AFTER mesa because OpenGL doesn't initialize itself, you need a library like one of these to do it. Both of these are cross platform too.

Best of luck!

You might be interested in...

[http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/) (A couple of OpenGL examples with SDL)
[http://www.lighthouse3d.com/opengl/glut/](http://www.lighthouse3d.com/opengl/glut/) (Thorough explanation of GLUT)
[http://nehe.gamedev.net/](http://nehe.gamedev.net/) (has Linux+SDL and glut downloads, with makefiles to compile)
[http://p13.wikispaces.com/Cpp](http://p13.wikispaces.com/Cpp) (A couple of examples I've written)

---

### Post by Cesa on 2007-02-28
Hi, I'm trying to get OpenGL programming going, using Eclipse and glut. However, it doesn't work, I am using aaindex from the [red book]("http://opengl.org/resources/code/samples/redbook/") as a test, I include:

```

#include <stdlib.h>
#include <stdio.h>
#include <GL/glew.h>
#include <GL/glut.h>
```

but get errors like:

```

../main.cpp:140: undefined reference to `glutPostRedisplay'
../main.cpp:122: undefined reference to `glLoadIdentity'
../main.cpp:125: undefined reference to `gluOrtho2D'
```

I get an error for each call to any gl, glu or glut function. I added the option -lglut for g++ (I let Eclipse handle compiling, linking etc., but I read somewhere the -lglut option was necessary)

Note that the -h files are all found, no warnings there.

What am I missing?

---

### Post by runningwithscissors on 2007-02-28
> **Cesa said:**
> I get an error for each call to any gl, glu or glut function. I added the option -lglut for g++ (I let Eclipse handle compiling, linking etc., but I read somewhere the -lglut option was necessary)

Note that the -h files are all found, no warnings there.

What am I missing?
Linker not finding the glut library. If there is a way, check the exact command Eclipse CDT is using to compile your program, or compile on the command line with
```
$ gcc <program.c> -o <binary> -lglut
```
and see.

---

### Post by Cesa on 2007-02-28
Right now I feel really stupid, I simply added "-lglut" in the wrong place...

Though now that *that* works, I get another error:

```

freeglut (/media/D/MyDocuments/Exjobb/GPUtest/Debug/GPUTest):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  14
  Current serial number in output stream:  17
```

:???:

I'll search for solutions, as well as trying a different example, but meanwhile if someone has a suggestion, shoot.

---

### Post by runningwithscissors on 2007-02-28
> **Cesa said:**
> Right now I feel really stupid, I simply added "-lglut" in the wrong place...

Though now that *that* works, I get another error:

```

freeglut (/media/D/MyDocuments/Exjobb/GPUtest/Debug/GPUTest):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  14
  Current serial number in output stream:  17
```

:???:

I'll search for solutions, as well as trying a different example, but meanwhile if someone has a suggestions, shoot.

It could be due to your X server not supporting the glX extensions. Do you have the glx module loaded and are you using a display driver (and card) that supports OpenGL?

---

### Post by Cesa on 2007-02-28
> **runningwithscissors said:**
> It could be due to your X server not supporting the glX extensions. Do you have the glx module loaded and are you using a display driver (and card) that supports OpenGL?

I have a nvidia Quadro FX 3450/4000 card with nvidias driver installed. I'm new to Ubuntu (and Linux), so I'm not sure how to know if a glx module is loaded or not. In the nvidia X server settings program there is a section called OpenGL/GLX information that says: "Direct Rendering: Yes", if that's what you mean.

---

### Post by runningwithscissors on 2007-02-28
> **Cesa said:**
> In the nvidia X server settings program there is a section called OpenGL/GLX information that says: "Direct Rendering: Yes", if that's what you mean.
Then you're all right.

What parameters are you passing to glutInitDisplayMode?

---

### Post by Cesa on 2007-02-28
> **runningwithscissors said:**
> Then you're all right.

What parameters are you passing to glutInitDisplayMode?

GLUT_SINGLE | GLUT_INDEX

The program fails at glutCreateWindow (might be obvious from the error I guess)

Ok, I tried changing GLUT_INDEX to GLUT_RGBA, and than the program runs, still not sure what the problem is though.

---

### Post by Cesa on 2007-02-28
Ok, anyway, all I wanted to do was to get OpenGL running, which it does now, I don't need that specific example to work. The difference between GLUT_INDEX and GLUT_RGBA is something I just have to read up on, and *if* I need index I will deal with that problem then.

Thanks for your help.

---


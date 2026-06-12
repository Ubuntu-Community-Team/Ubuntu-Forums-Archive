---
title: "can't compile nehe tutorial"
date: 2006-08-02
forum: Packaging and Compiling Programs
---

### Post by Choad on 2006-08-02
i get the following error

> 
richard@richard-laptop:/media/c/Documents and Settings/Richard/Desktop/New Folder$ make
gcc -Wall -I/usr/include/   -c -o lesson4.o lesson4.c
lesson4.c: In function ‘keyPressed’:
lesson4.c:110: warning: implicit declaration of function ‘exit’
lesson4.c:110: warning: incompatible implicit declaration of built-in function ‘exit’
gcc -Wall -I/usr/include/ -o lesson4 -L/usr/X11R6/lib  lesson4.o -lX11 -lXi -lXmu -lglut -lGL -lGLU -lm
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
make: *** [lesson4] Error 1
rm lesson4.o


i got a lot of other errors before, but i read through and installed glut and mesa - that solved a lot of the errors, but now i am left with this and i dont know what to do

i am trying to compile [this](http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=04) tutorial (using [this](http://nehe.gamedev.net/data/lessons/linux/lesson04.tar.gz) source code)

please help!

---

### Post by Choad on 2006-08-02
i fixed that myself, but now i am compiling a different one and it says i don't have gl.h apparently

> 
checking for gl.h... no
configure: error: OpenGL headers not found


what package do i need for that?

---

### Post by lgoss007 on 2006-08-05
Did you figure this out?

I think the one you want is:
libgl1-mesa-dev

---

### Post by Choad on 2006-08-05
ty very much! ill try that out in a min

damn wireless suport.... if it was only there i wouldnt bother with windows. i cant remember the last time i played a game and openGL programming in linux is SOOOOOOOOOOOOO much easier than in windows

GLUT is ftw, ~140 lines for linux vs. ~430 lines of code in windows... stupid win32 API....

</rant>

anyway thx for that ill try it out when i go downstairs and wire up my laptop

---

### Post by Choad on 2006-08-05
ok, apparently its mesa-common-dev that i need. i cant apt-get it for some reason.... repo? but i downloaded it manually and installed it, and *STILL* i get the same error!

could it be that the ./configure script is looking in the wrong place for it??

---

### Post by lgoss007 on 2006-08-11
Doh, sorry I'm a little slow at replying (old email address was being used)...

Anyways, if you haven't solved the problem yet...

Strange that you can't apt-get mesa-common-dev, I'm pretty sure it's in the main repositories under the Development section (can you see it in synaptic?).

If you downloaded manually and installed it, it probably installed to /usr/local (unless you changed it in configure), in which case you'd need to add that directory to your compiler options (-L/usr/local for make, other tools have similar options).

---


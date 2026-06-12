---
title: "How to Pull everything together?"
date: 2009-01-25
forum: Programming Talk
---

### Post by prasath_amd on 2009-01-25
Ok, I've downloaded the MesaLib Tar files & extracted them to:-

/home/prasath/SW_Pack/Mesa-7.3

now how can i compile a Simple C-Based OpenGL-UT Program?. 

I'm running "Ubuntu 8.10-i386". So its an "x86" version right?. So I used the "make linux-x86" command to build the lib files. But I don't know where the lib files are created after the build.

I used this command at the terminal:-

$ gcc hello.c -o hello -I/home/prasath/SW_Pack/Mesa-7.3/include

it successfully included the <GL/glut.h> file. But when i use a function inside the program, like the "glutInitDisplayMode()" it produces an "undefined unreferenced" error. I've googled a bit and found that I need to specify where the lib files are located to the compiler. But I don't know where the lib files are located. Plz Help.

---

### Post by slavik on 2009-01-25
no need todownload Mesa, the Mesa libraries are in the repositories, you can search for libmesa and freeglut. search google for "nehe opengl", these are nice opengl tutorials.

---


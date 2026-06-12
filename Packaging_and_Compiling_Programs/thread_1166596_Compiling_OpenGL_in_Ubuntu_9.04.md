---
title: "Compiling OpenGL in Ubuntu 9.04"
date: 2009-05-21
forum: Packaging and Compiling Programs
---

### Post by cwar on 2009-05-21
So I'm trying to compile a very simple OpenGL app in Ubuntu 9.04. The code is:

```
#include <GL/glut.h>

void mydisplay(){
    glClear(GL_COLOR_BUFFER_BIT); //clear the color buffer
    glBegin(GL_POLYGON);
        glVertex2f(-0.5, -0.5);
        glVertex2f(-0.5, 0.5);
        glVertex2f(0.5, 0.5);
        glVertex2f(0.5, -0.5);
    glEnd();
    glFlush();
}

int main(int argc, char** argv) {
    glutCreateWindow("simple");
    glutDisplayFunc(mydisplay);
    glutMainLoop();
}
```And when I try to compile using

```
gcc simple.c
```I get the following output in the terminal

```
/tmp/ccpoeTpT.o: In function `mydisplay':
simple.c:(.text+0xe): undefined reference to `glClear'
simple.c:(.text+0x1a): undefined reference to `glBegin'
simple.c:(.text+0x30): undefined reference to `glVertex2f'
simple.c:(.text+0x46): undefined reference to `glVertex2f'
simple.c:(.text+0x5c): undefined reference to `glVertex2f'
simple.c:(.text+0x72): undefined reference to `glVertex2f'
simple.c:(.text+0x77): undefined reference to `glEnd'
simple.c:(.text+0x7c): undefined reference to `glFlush'
/tmp/ccpoeTpT.o: In function `main':
simple.c:(.text+0x9b): undefined reference to `glutCreateWindow'
simple.c:(.text+0xa8): undefined reference to `glutDisplayFunc'
simple.c:(.text+0xad): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status

```Obviously it isn't finding the openGL libraries. I have the following installed:

glutg3, libglut3-dev, freeglut3-dev, freeglut3

And any dependencies.

Anyone have any idea what I'm missing?

This is probably a very basic question, but I am very new to compiling in Ubuntu (and command line at all, used visual studio in windows up to this point) and even newer to openGL (I'm a student, just started the graphics class). I apologize if this is too easy, I tried searching the forums and google but was unsuccesful. Also, this is my first post here on these forums so also let me know if I am missing anything, posting in the wrong place or doing anything wrong.

Thanks!

---

### Post by moma on 2009-05-23
Hello and welcome.

Compile and link your code to libGL and libglut libraries, like this

$ [COLOR="SeaGreen"]gcc -lGL  -lglut simple.c -o simple[/COLOR]

Run it 
$ [COLOR="SeaGreen"]./simple[/COLOR]

You may also need libxmu-dev and libxxf86vm-dev packages.

Add also [COLOR="SeaGreen"]glutInit(&argc, argv);[/COLOR] as the first line in main().

Plus read this guide: [http://www.futuredesktop.org/codeblocks_on_ubuntu_9.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_9.04.html)
Espesially the Notes **3)** and **5)** are important.

Learn also to download and compile the examples from nehe.gamedev.net.
See: [http://ubuntuforums.org/showthread.php?p=2868563#post2868563](http://ubuntuforums.org/showthread.php?p=2868563#post2868563)

EDIT: [this...]("http://ubuntuforums.org/showthread.php?t=1174975") posting contains some nice details.

---


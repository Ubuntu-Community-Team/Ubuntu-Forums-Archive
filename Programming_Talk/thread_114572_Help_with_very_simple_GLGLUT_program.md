---
title: "Help with very simple GL/GLUT program"
date: 2006-01-08
forum: Programming Talk
---

### Post by bigdufstuff on 2006-01-08
I am following a tutorial for OpenGL on Linux found here

[http://mercury.chem.pitt.edu/~sasha/LinuxFocus/English/January1998/article16.html](http://mercury.chem.pitt.edu/~sasha/LinuxFocus/English/January1998/article16.html)

I am trying to get this simple example to compile

```

#include <GL/glut.h>

int main(int argcp, char **argv) { 

  /* Set window size and location */
  glutInit(&argcp, argv);
  glutInitWindowSize(640, 480);
  glutInitWindowPosition(0, 0);
  
  /* Select type of Display mode:
     single buffer & RGBA color */
  glutInitDisplayMode(GLUT_RGBA | GLUT_SINGLE);

  /*Initialize GLUT state */

  glutCreateWindow("Hello World");

  glutMainLoop();

  return 0;

}

```

gcc barfs with this

```

$ gcc glexample.c
/tmp/ccoHHIVb.o: In function `main':
glexample.c:(.text+0x27): undefined reference to `glutInit'
glexample.c:(.text+0x3c): undefined reference to `glutInitWindowSize'
glexample.c:(.text+0x4b): undefined reference to `glutInitWindowPosition'
glexample.c:(.text+0x58): undefined reference to `glutInitDisplayMode'
glexample.c:(.text+0x68): undefined reference to `glutCreateWindow'
glexample.c:(.text+0x70): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status

```

Am I missing a GLUT package? or is there something wrong with the code? I can't tell.

I installed the following glut packages

freeglut3-dev
glutg3-dev
libglut3-dev

on top of this I also installed the mesa development package.
Any idea why it won't compile? thanks.

---

### Post by lnostdal on 2006-01-08
You must tell GCC what libraries it should link with, with these messages it is telling you that it can't find any of the symbols mentioned in any of the files or libraries it currently links with. Use -l to specify library, and -L to specify search-paths for libraries.

Something like this (I think): gcc -lglut glexample.c -o glexample

edit:
also, take a look at this very good resource for learning how to use GCC for compiling/linking C and C++-programs:
[http://www.network-theory.co.uk/docs/gccintro/gccintro_17.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_17.html)

---

### Post by Lews Therin on 2006-01-08
You must link in the GLUT libraries. You'll have something in /usr/lib called libglut-something, so add -lglut-something to your gcc flags. You'll have to do the same when you add OpenGL functions to your program, but with libopengl32

---

### Post by bigdufstuff on 2006-01-08
[QUOTE=lnostdal]You must tell GCC what libraries it should link with, with these messages it is telling you that it can't find any of the symbols mentioned in any of the files or libraries it currently links with. Use -l to specify library, and -L to specify search-paths for libraries.

Something like this (I think): gcc -lglut glexample.c -o glexample

edit:
also, take a look at this very good resource for learning how to use GCC for compiling/linking C and C++-programs:
[http://www.network-theory.co.uk/docs/gccintro/gccintro_17.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_17.html)[/QUOTE]


awesome that worked, thanks! and thank you for the link.

---


---
title: "OpenGL"
date: 2007-08-08
forum: Programming Talk
---

### Post by urgo on 2007-08-08
Hello,

I would like to start programing with OpenGl.

I found that code:

```


//*** rect *****
#include <GL/gl.h>
#include <GL/glut.h>
void display(void)
{
/* clear all pixels */
glClear (GL_COLOR_BUFFER_BIT);
/* draw white polygon (rectangle) with corners at
* (0.25, 0.25, 0.0) and (0.75, 0.75, 0.0)
*/
glColor3f (1.0, 1.0, 1.0);
glBegin(GL_POLYGON);
glVertex3f (0.25, 0.25, 0.0);
glVertex3f (0.75, 0.25, 0.0);
glVertex3f (0.75, 0.75, 0.0);
glVertex3f (0.25, 0.75, 0.0);
glEnd();
/* don’t wait!
* start processing buffered OpenGL routines
*/
glFlush ();
}
void init (void)
{
/* select clearing (background) color */
glClearColor (0.0, 0.0, 0.0, 0.0);
/* initialize viewing values */
glMatrixMode(GL_PROJECTION);
glLoadIdentity();
glOrtho(0.0, 1.0, 0.0, 1.0, -1.0, 1.0);
}
/*
* Declare initial window size, position, and display mode
* (single buffer and RGBA). Open window with "hello"
* in its title bar. Call initialization routines.
* Register callback function to display graphics.
* Enter main loop and process events.
*/
int main(int argc, char** argv)
{
glutInit(&argc, argv);
glutInitDisplayMode (GLUT_SINGLE | GLUT_RGB);
glutInitWindowSize (250, 250);
glutInitWindowPosition (100, 100);
glutCreateWindow ("hello");
init ();
glutDisplayFunc(display);
glutMainLoop();
return 0; /* ISO C requires main to return int. */
}


```

whilst compiling I received:

```


xxx@xxx$ g++-4.1 rect.cc -o rect
/tmp/ccn7Tz5S.o: In function `init()':
hello.cc:(.text+0x2a): undefined reference to `glClearColor'
hello.cc:(.text+0x36): undefined reference to `glMatrixMode'
hello.cc:(.text+0x3b): undefined reference to `glLoadIdentity'
hello.cc:(.text+0x67): undefined reference to `glOrtho'
/tmp/ccn7Tz5S.o: In function `main':
hello.cc:(.text+0x8a): undefined reference to `glutInit'
hello.cc:(.text+0x96): undefined reference to `glutInitDisplayMode'
hello.cc:(.text+0xaa): undefined reference to `glutInitWindowSize'
hello.cc:(.text+0xbe): undefined reference to `glutInitWindowPosition'
hello.cc:(.text+0xca): undefined reference to `glutCreateWindow'
hello.cc:(.text+0xdb): undefined reference to `glutDisplayFunc'
hello.cc:(.text+0xe0): undefined reference to `glutMainLoop'
/tmp/ccn7Tz5S.o: In function `display()':
hello.cc:(.text+0x100): undefined reference to `glClear'
hello.cc:(.text+0x11f): undefined reference to `glColor3f'
hello.cc:(.text+0x12b): undefined reference to `glBegin'
hello.cc:(.text+0x14a): undefined reference to `glVertex3f'
hello.cc:(.text+0x169): undefined reference to `glVertex3f'
hello.cc:(.text+0x188): undefined reference to `glVertex3f'
hello.cc:(.text+0x1a7): undefined reference to `glVertex3f'
hello.cc:(.text+0x1ac): undefined reference to `glEnd'
hello.cc:(.text+0x1b1): undefined reference to `glFlush'
collect2: ld returned 1 exit status


```

I have installed the following libraries:
freeglut3; freeglut3-dev; glutg3; glutg3-dev; libglut3; libglut3-dev

Where is the problem? :(

---

### Post by Wybiral on 2007-08-08
You need to link to the libraries when compiling.

Try compiling with this command:

```

g++ rect.cc -o rect -lGLU -lGL -lglut

```

---

### Post by urgo on 2007-08-08
You are great !  Thank`s

---


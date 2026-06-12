---
title: "C++: OpenGL Clear"
date: 2010-03-20
forum: Programming Talk
---

### Post by Velovix on 2010-03-20
Let me try to explain my dilemma as clearly as I can. For the record, I am using Ubuntu 8.04.4 LTS (Sorry), g++ (obviously), and Eclipse C/C++ IDE, although I've tried it purely through the terminal as well.

I'm a somewhat new C++ programmer, and I've been programming with terminals for a while now. You can do a lot with that, but I've wanted to make my programs graphic.
I decided to use "glut" library along with OpenGL.
Anyway, I found a basic example for creating a simple window using glut and opengl (I added a bunch of #includes to it. Those are all the files I have in /usr/include/GL/):
```

/* Demo.cpp
 * A simple OpenGL program using GLUT.  It creates a blank black
 * window which can be used as a starting point for OpenGL programming.
 *
 * Link in opengl32, glu32, and glut32 libraries and make sure to include
 * windows.h if you are compiling with Eclipse in Windows.
 *
 * Author: Paul Solt  3-4-07
 * Based on examples from the Red book OpenGL Programming Guide
 */
#include <GL/gl.h>
#include <GL/glut.h>
#include <GL/glext.h>
#include <GL/gl_mangle.h>
#include <GL/glu.h>
#include <GL/glx.h>
#include <GL/glx_mangle.h>
#include <GL/glu_mangle.h>
#include <GL/glxext.h>
#include <GL/freeglut.h>
#include <GL/freeglut_ext.h>
#include <GL/freeglut_std.h>



const int WIDTH = 600;
const int HEIGHT = 480;

/* Prototypes */
void init();
void display();

/* Definitions */

/* Initializes the OpenGL state */
void init() {
    glClearColor( 0.0, 0.0, 0.0, 1.0 ); /* Set the clear color */
}

/* Displays a black clear screen */
void display() {
    glClear( GL_COLOR_BUFFER_BIT ); /* Clear the screen with the clear color */
    glutSwapBuffers(); /* Double buffering */
}

/* The main function */
int main( int argc, char *argv[] ) {
    /* Glut setup function calls */
    glutInit( &argc, argv );
    glutInitDisplayMode( GLUT_DOUBLE | GLUT_RGB ); /* Use double buffering and RGB colors */
    glutInitWindowPosition( 100, 100 );
    glutInitWindowSize( WIDTH, HEIGHT );
    glutCreateWindow( argv[0] );
    init();
    glutDisplayFunc( display );  /* Call back display function */
    glutMainLoop(); /* Continue drawing the scene */
    return 0;
}

```Everything seems to work dandy except for "glClearColor();" and "glClear();". It basically says that "It was not declared in this scope" which usually means that I don't have the correct libraries, but the weird part is that they call "glClearColor" "mglClearColor", and "glClear();" "mglClear();".

I have no idea where G++ get's the m's, but I presume that's the problem. I checked "gl.h" to see if the commands were there, and they were, but obviously not with the m's. If you would like me to ellaborate, or try to explain better, please don't hesitate to ask. I know enough to make some assumptions, but please do not skip steps.

Thanks,
         Velovix

---

### Post by Velovix on 2010-03-21
Bump.

---

### Post by Zugzwang on 2010-03-22
Short answer: Do not include the header files concerned with "name mangling", i.e., "GL/gl_mangle.h", "GL/glx_mangle.h" and "GL/glu_mangle.h". They contain macros for renaming these functions. The header files say that they are somewhat good for compatibility but I have no clue what happens there.

---

### Post by Velovix on 2010-03-22
Cool, thanks. I'll try that tonight.

---

### Post by Senesence on 2010-03-22
You should include only the headers you need at the moment, not everything you find under "/usr/include/GL".

The only header you need to include (for the code you posted) is glut.h.

You can/should remove all others.

---

### Post by Velovix on 2010-03-22
OK, so I fixed it up based on what you recommended, and it fixed the current problem, but my next problem, something that's been coming up quite a bit, is this problem with arguments.
```

#include <GL/glut.h>

const int WIDTH = 600;
const int HEIGHT = 480;

using namespace std;
void init();
void display();

void init() {
    glClearColor( 0.0, 0.0, 0.0, 1.0 );
}

void display() {
    glClear( GL_COLOR_BUFFER_BIT );
    glutSwapBuffers();
}

int main(int argc, const char* argv[]) {
@    glutInit( &argc, argv );
    glutInitDisplayMode( GLUT_DOUBLE | GLUT_RGB ); /* Use double buffering and RGB colors */
    glutInitWindowPosition( 100, 100 );
    glutInitWindowSize( WIDTH, HEIGHT );
    glutCreateWindow( argv[0] );
    init();
    glutDisplayFunc( display );  /* Call back display function */
    glutMainLoop(); /* Continue drawing the scene */
    return 0;
}


```
It says there is an "invalid conversion from ‘const char**’ to ‘char**’" on the line I marked with an @. Any suggestions?

---

### Post by DougB1958 on 2010-03-22
> **Velovix said:**
> It says there is an "invalid conversion from ‘const char**’ to ‘char**’" on the line I marked with an @. Any suggestions?

Try removing the "const" from the declaration of argv. If I remember right, glutInit may change argv (e.g., to remove window-system-related switches that it processes).

---

### Post by Velovix on 2010-03-22
> **DougB1958 said:**
> Try removing the "const" from the declaration of argv. If I remember right, glutInit may change argv (e.g., to remove window-system-related switches that it processes).
I wish it was that simple. All that does is give me a whole plethora of errors. Anything else I can do?

---

### Post by Garibaldi_nZ on 2010-03-23
Hey, yeah you just need to cast the const char** to a char**. This means that the function receiving the char** is able to change the value of the pointer (which is generally a silly thing to do). What compiler are you using? GCC seems to treat this conversion as a warning by default if you omit the cast.

Checkout this simple program for details.

```

#include <stdio.h>

void func (int argc, char** argv) {
	int i = 0;
	for (; i < argc; i++) {
		printf("%s\n", argv[i]);
	}
}

int main (int argc, const char** argv) {
	func (argc, (char**)argv);
}

```

---

### Post by Velovix on 2010-03-25
I am using GCC. How can I get around that issue?

---

### Post by Velovix on 2010-03-25
Bump. These forums are so active! My thread gets buried in a day!

---

### Post by Zugzwang on 2010-03-26
> **Velovix said:**
> Bump. These forums are so active! My thread gets buried in a day!

There are two reasons for this:
[LIST]
[*]You said that for DougB1958's solution, you get a lot of errors, but you did not copy&paste them here. Do so such that everyone known why things do not work!
[*]Garibaldi_nZ posted another solution, which you did not comment on. So if you want an answer you should clarify what is wrong with his/her solution. To me, both solutions look ok.
[/LIST]

---

### Post by Velovix on 2010-03-26
> **Zugzwang said:**
> There are two reasons for this:
[LIST]
[*]You said that for DougB1958's solution, you get a lot of errors, but you did not copy&paste them here. Do so such that everyone known why things do not work!
[*]Garibaldi_nZ posted another solution, which you did not comment on. So if you want an answer you should clarify what is wrong with his/her solution. To me, both solutions look ok.
[/LIST]

Hey, I wasn't complaining. I love this forum so far.

Well for the first one, I meant the program didn't find anything as a valid command. I didn't find it neccisary to post all of the errors, when they all just mean "You completely broke the program". But to be fair, I could have been more specific.

It seemed to me that Garibaldi_nZ was explaining arguments more then anything else, and I addressed his question on whether or not I was using GCC.

It doesn't matter anyway, I tried it on a new compiler, and that fixed the problem. Thanks guys!

---


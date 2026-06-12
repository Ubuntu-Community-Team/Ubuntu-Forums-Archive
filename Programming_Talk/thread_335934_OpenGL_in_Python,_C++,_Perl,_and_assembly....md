---
title: "OpenGL in Python, C++, Perl, and assembly..."
date: 2007-01-10
forum: Programming Talk
---

### Post by Wybiral on 2007-01-10
To demonstrate the similarity between a few common languages...



C++
```

//
//
//
#include <GL/glut.h>   

int angle = 0;

void InitGL(int width, int height) {
	//
	glMatrixMode(GL_PROJECTION);
	gluPerspective(45.0, (float)width/height, 0.1, 100.0);
	glMatrixMode(GL_MODELVIEW);
	glEnable(GL_DEPTH_TEST);
}

void DrawGLScene() {

	glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT); 
	glLoadIdentity();
	glTranslatef(0.0, 0.0, -6.0); 
	glRotatef(angle, 1.0, 1.0, 0.0); 
	glRotatef(angle, 0.0, 1.0, 0.0); 
	glBegin(GL_QUADS);
	glColor3f(1,0,0); glVertex2f( 1.0,-1.0);
	glColor3f(1,1,0); glVertex2f(-1.0,-1.0);
	glColor3f(1,1,1); glVertex2f(-1.0, 1.0);
	glColor3f(0,0,1); glVertex2f( 1.0, 1.0);
	glEnd();
	angle += 1; 
	glutSwapBuffers();
}

int main(int argc, char** argv) {
	glutInit(&argc, argv);
	glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH); 
	glutInitWindowSize(640, 480); 
	glutCreateWindow("OpenGL in C++"); 
	glutIdleFunc(&DrawGLScene);
	InitGL(640, 480);
	glutMainLoop(); 
}

//

```

Perl
```

#
#
#
use OpenGL qw(:all);

my $angle = 0;

sub InitGL {
	my ($width, $height) = @_;
	glMatrixMode(GL_PROJECTION);
	gluPerspective(45.0, $width/$height, 0.1, 100.0);
	glMatrixMode(GL_MODELVIEW);
	glEnable(GL_DEPTH_TEST);
}

sub DrawGLScene {

	glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT); 
	glLoadIdentity;
	glTranslatef(0.0, 0.0, -6.0); 
	glRotatef($angle, 1.0, 1.0, 0.0); 
	glRotatef($angle, 0.0, 1.0, 0.0); 
	glBegin(GL_QUADS);
	glColor3f(1,0,0); glVertex2f( 1.0,-1.0);
	glColor3f(1,1,0); glVertex2f(-1.0,-1.0);
	glColor3f(1,1,1); glVertex2f(-1.0, 1.0);
	glColor3f(0,0,1); glVertex2f( 1.0, 1.0);
	glEnd;
	$angle += 1; 
	glutSwapBuffers;
}

sub main {
	glutInit;
	glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH); 
	glutInitWindowSize(640, 480); 
	glutCreateWindow("OpenGL in Perl"); 
	glutIdleFunc(\&DrawGLScene);
	InitGL(640, 480);
	glutMainLoop; 
}

main();

```

Python
```

import sys
from OpenGL.GL import *
from OpenGL.GLUT import *
from OpenGL.GLU import *

angle = 0

def InitGL(width, height):
	#
	glMatrixMode(GL_PROJECTION)
	gluPerspective(45.0, float(width)/height, 0.1, 100.0)
	glMatrixMode(GL_MODELVIEW)
	glEnable(GL_DEPTH_TEST)


def DrawGLScene():
	global angle
	glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT)
	glLoadIdentity()
	glTranslatef(0.0, 0.0, -6.0)
	glRotatef(angle, 1.0, 1.0, 0.0)
	glRotatef(angle, 0.0, 1.0, 0.0)
	glBegin(GL_QUADS)
	glColor3f(1,0,0); glVertex2f( 1.0,-1.0)
	glColor3f(1,1,0); glVertex2f(-1.0,-1.0)
	glColor3f(1,1,1); glVertex2f(-1.0, 1.0)
	glColor3f(0,0,1); glVertex2f( 1.0, 1.0)
	glEnd()
	angle += 1
	glutSwapBuffers()


def main():
	glutInit(sys.argv)
	glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH)
	glutInitWindowSize(640, 480)
	glutCreateWindow("OpenGL in Python")
	glutIdleFunc(DrawGLScene)
	InitGL(640, 480)
	glutMainLoop()


main()

```

And just for fun, I disassembled the C version, optimized it a little, added some comments...
Gas Assembly
```

### Constants ###
.constTitle:
	.string	"OpenGL in GAS Assembly"
.constOneTenth:
	.long	-1717986918
	.long	1069128089
.constAspectRatio:
	.long	343597384
	.long	1073039278
.constFOV:
	.long	0
	.long	1078362112

### Variables ###
.globl angle
	.bss
	.size	angle, 4
angle:
	.text

### Functions ###
.globl DrawGLScene
.globl main

DrawGLScene:
	pushl	%ebp
	movl	%esp, %ebp
	subl	$24, %esp
	movl	$16640, (%esp) #\__glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT)
	call	glClear        #/
	call	glLoadIdentity #\__glLoadIdentity()
	movl	$0xc0c00000, 8(%esp) #\
	movl	$0x00000000, 4(%esp) # \__glTranslatef(0, 0, -6)
	movl	$0x00000000, (%esp)  # /
	call	glTranslatef         #/
	pushl	angle                 #\
	fildl	(%esp)                # \
	leal	4(%esp), %esp         #  \
	movl	$0x00000000, 12(%esp) #   \__glRotatef(angle, 1, 1, 0)
	movl	$0x3f800000, 8(%esp)  #   /
	movl	$0x3f800000, 4(%esp)  #  /
	fstps	(%esp)                # /
	call	glRotatef             #/
	pushl	angle                 #\
	fildl	(%esp)                # \
	leal	4(%esp), %esp         #  \
	movl	$0x00000000, 12(%esp) #   \__glRotatef(angle, 0, 1, 0)
	movl	$0x3f800000, 8(%esp)  #   /
	movl	$0x00000000, 4(%esp)  #  /
	fstps	(%esp)                # /
	call	glRotatef             #/
	movl	$7, (%esp) #\__glBegin(GL_QUADS)
	call	glBegin    #/
	movl	$0, 8(%esp)  #\
	movl	$0, 4(%esp)  # \__glColor3b(127, 0, 0)
	movl	$127, (%esp) # /
	call	glColor3b    #/
	movl	$-1, 4(%esp) #\
	movl	$1, (%esp)   # \__glVertex2i(1, -1)
	call	glVertex2i   #/
	movl	$0, 8(%esp)   #\
	movl	$127, 4(%esp) # \__glColor3b(127, 127, 0)
	movl	$127, (%esp)  # /
	call	glColor3b     #/
	movl	$-1, 4(%esp) #\
	movl	$-1, (%esp)  # \__glVertex2i(-1,-1)
	call	glVertex2i   #/
	movl	$127, 8(%esp) #\
	movl	$127, 4(%esp) # \__glColor3b(127,127,127)
	movl	$127, (%esp)  # /
	call	glColor3b     #/
	movl	$1, 4(%esp) #\
	movl	$-1, (%esp) # \__glVertex2i(-1, 1)
	call	glVertex2i  #/
	movl	$127, 8(%esp) #\
	movl	$0, 4(%esp)   # \__glColor3b(0, 0, 127)
	movl	$0, (%esp)    # /
	call	glColor3b     #/
	movl	$1, 4(%esp) #\
	movl	$1, (%esp)  # \__glVertex2i(1, 1)
	call	glVertex2i  #/
	call	glEnd #\__glEnd()
	incl	angle #\__angle+=1
	call	glutSwapBuffers #\__glutSwapBuffers()
	leave
	ret

main:
	leal	4(%esp), %ecx
	andl	$-16, %esp
	pushl	-4(%ecx)
	pushl	%ebp
	movl	%esp, %ebp
	pushl	%ecx
	subl	$36, %esp
	movl	4(%ecx), %eax
	movl	%eax, 4(%esp) #\
	movl	%ecx, (%esp)  #	\__glutInit(&argc, argv)
	call	glutInit      #/
	movl	$18, (%esp)         #\__glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH)
	call	glutInitDisplayMode #/
	movl	$480, 4(%esp)      #\
	movl	$640, (%esp)       # \__glutInitWindowSize(640, 480)
	call	glutInitWindowSize #/
	movl	$.constTitle, (%esp) #\__glutCreateWindow(constTitle)
	call	glutCreateWindow     #/
	movl	$DrawGLScene, (%esp) #\__glutIdleFunc(DrawGLScene)
	call	glutIdleFunc         #/
	movl	$5889, (%esp) #\__glMatrixMode(GL_PROJECTION)
	call	glMatrixMode  #/
	movl $100, 24(%esp)     #\
	fldl	.constOneTenth    # \
	fstpl	16(%esp)          #  \
	fldl	.constAspectRatio #   \__gluPerspective(45, 1.33, 0.1, 100)
	fstpl	8(%esp)           #   /
	fldl	.constFOV         #  /
	fstpl	(%esp)            # /
	call	gluPerspective    #/
	movl	$5888, (%esp) #\__glMatrixMode(GL_MODELVIEW)
	call	glMatrixMode  #/
	movl	$2929, (%esp) #\__glEnable(GL_DEPTH_TEST)
	call	glEnable      #/
	call	glutMainLoop #\__glutMainLoop()

```

To compile the C++ one, "g++ program.cpp -lglut"
To run the perl one "perl program.pl"
To run the python one "python program.py"
To assembly the GAS one "gcc program.s -lglut -s"

You will need the appropriate OpenGL modules/libraries for those languages (but, the assembly one uses the C libraries)

These examples use GLUT as well, so you will need freeGLUT installed.

You can also cut a few bytes off of the assembly one with a hex editor, but for simplicity just assembly that code above.

With the C, perl, and python examples I preserved the spacing to show how they line up so well.

---

### Post by po0f on 2007-01-11
Wybiral,

Would you mind posting a couple of OpenGL links in the sticky at the top?  I know it's slightly off-topic (we're still talking about OpenGL, though  ;)), I'd just like a basic run-down of what I'm thinking of getting myself into.  Anything from what you would consider beginner to intermediate tutorials/guides/whatever would be nice.  TIA.  :)

Oh yeah, I'd prefer C++ or Python examples, if that influences your decision on what to post.

---

### Post by Wybiral on 2007-01-11
Ok, I'll try to put something together. I've also been thinking about adding an assembly section to that post too, seeing how no one else has (and doubtfully will). I've been using OpenGL for a while now so I should have some good bookmarks/links laying around somewhere.

---

### Post by Wybiral on 2007-01-11
Ok, I put some of my favorite OpenGL links on the "how to start programming" thread.

---

### Post by Grey on 2007-01-11
I really don't think that OpenGL is a good example for showing the differences between languages.  OpenGL is a very very specific library, and the function calls and usage will be nearly identical, regardless of the language used, as that's just how it works.  (Unless you are able to figure out a way of doing it with something weird, like Scheme or Prolog).

But yeah, it's rather amusing to see how identical it all is when you are using a common library.  The real differences will begin to show themselves though, when you start writing code around that very basic stuff.

---

### Post by Wybiral on 2007-01-11
> I really don't think that OpenGL is a good example for showing the differences between languages. OpenGL is a very very specific library, and the function calls and usage will be nearly identical, regardless of the language used, as that's just how it works. (Unless you are able to figure out a way of doing it with something weird, like Scheme or Prolog).

But yeah, it's rather amusing to see how identical it all is when you are using a common library. The real differences will begin to show themselves though, when you start writing code around that very basic stuff.

Yeah, I'm aware, OpenGL is OpenGL in any language... I just posted it to show the same example in different languages so it might make it easier for people who know one of them to see how it is done in the others.

---

### Post by bfree on 2007-06-06
> **Grey said:**
> I really don't think that OpenGL is a good example for showing the differences between languages.

It may not be the best way to demonstrate language differences, but it's a good way to demonstrate performance differences between language bindings - particularly in the use of vertex arrays.

Perl has very low overhead when interfacing with C libraries like OpenGL; as a result, there's very little difference between C and Perl performance.

Other language bindings, such as Python's PyOpenGL, introduce significant overhead, resulting in poor performance.  Python in particular suffers from performance issues related to array handling.  Various modules (ctypes) and Python enhancements (NumPy) have been introduced to improve Python array performance - but it still suffers in comparison to C/C++ or Perl.

You can read PyOpenGL's author explaining why Python is slower, and see C vs Perl and Perl vs Python benchmarks at [http://graphcomp.com/opengl/benchmarks](http://graphcomp.com/opengl/benchmarks)

I hope to post ruby benchmarks shortly.

---


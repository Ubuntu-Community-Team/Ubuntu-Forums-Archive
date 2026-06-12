---
title: "Starting off with OpenGL Programming"
date: 2005-11-16
forum: Programming Talk
---

### Post by mitchy_g on 2005-11-16
Hi,
I have been researching how to setup OpenGL on my Breezy box for a few days now. However I have had little success because I am a new to linux and alot of the information I have found is either for Windows or too ambiguos for me to get  a sample program running.

So to help solve my problems I started out by installing the following packages:

_Mesa 3d:_
libgl1-mesa
libgl1-mesa-dev
libglu1-mesa


_GL & Others:_
glutg3
glutg3-dev
libglui-dev
libglut3
libglut3-dev

My first questions at this point are; Mesa isnt an official release from the creators of OpenGL, is Mesa the only option I have to code somthing that "resembles" opengl in linux?

What is the difference between the glut3 packages and the libglut packages?

Is there anything else I need?

I eventually found this page: [HERE]("http://www.ece.eps.hw.ac.uk/~dml/cgonline/hyper00/openglcomp.html")
Which shows a few examples of how to use gcc or g++ to compile using Mesa and GLUT using the following in the command line:

```
# shell script to compile a Mesa program using the glut library
# on a Linux PC using C++
g++  myapp.cpp  -lglut -ffast-math  -lMesaGLU -lMesaGL -lm -L/usr/X11/lib \
-L/usr/X11R6/lib -lX11 -lXext -lXmu -lXt -lXi -lSM -lICE -o myapp]
``` 

however the compiler says that /usr/X11/lib does not exist, so i edited it to where the X11 folder is: /usr/X11R6/lib/X11

I eventually had the thing compiling but linker errors would arise.

THis is the code i was using: [Taken from NeHe at gamedev]("http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=02")
```
//
// This code was created by Jeff Molofee '99 (ported to Linux/GLUT by Richard Campbell '99)
//  
// If you've found this code useful, please let me know.
//  
// Visit me at www.demonews.com/hosted/nehe 
// (email Richard Campbell at ulmont@bellsouth.net)
//  
#include <GL/glut.h>    // Header File For The GLUT Library 
#include <GL/gl.h>	// Header File For The OpenGL32 Library
#include <GL/glu.h>	// Header File For The GLu32 Library
#include <unistd.h>     // Header File For sleeping.
    
/* ASCII code for the escape key. */
#define ESCAPE 27
    
/* The number of our GLUT window */
int window; 
    
/* A general OpenGL initialization function.  Sets all of the initial parameters. */
void InitGL(int Width, int Height)	        // We call this right after our OpenGL window is created.
{   
  glClearColor(0.0f, 0.0f, 0.0f, 0.0f);	// This Will Clear The Background Color To Black
  glClearDepth(1.0);				// Enables Clearing Of The Depth Buffer
  glDepthFunc(GL_LESS);				// The Type Of Depth Test To Do
  glEnable(GL_DEPTH_TEST);			// Enables Depth Testing
  glShadeModel(GL_SMOOTH);			// Enables Smooth Color Shading
    
  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();				// Reset The Projection Matrix
    
  gluPerspective(45.0f,(GLfloat)Width/(GLfloat)Height,0.1f,100.0f);	// Calculate The Aspect Ratio Of The Window
    
  glMatrixMode(GL_MODELVIEW);
}   
    
/* The function called when our window is resized (which shouldn't happen, because we're fullscreen) */
void ReSizeGLScene(int Width, int Height)
{   
  if (Height==0)				// Prevent A Divide By Zero If The Window Is Too Small
    Height=1;
    
  glViewport(0, 0, Width, Height);		// Reset The Current Viewport And Perspective Transformation
    
  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();
    
  gluPerspective(45.0f,(GLfloat)Width/(GLfloat)Height,0.1f,100.0f);
  glMatrixMode(GL_MODELVIEW);
}   
    
/* The main drawing function. */
void DrawGLScene()

{   
  glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);		// Clear The Screen And The Depth Buffer
  glLoadIdentity();				// Reset The View
    
  glTranslatef(-1.5f,0.0f,-6.0f);		// Move Left 1.5 Units And Into The Screen 6.0
	
  // draw a triangle
  glBegin(GL_POLYGON);				// start drawing a polygon
  glVertex3f( 0.0f, 1.0f, 0.0f);		// Top
  glVertex3f( 1.0f,-1.0f, 0.0f);		// Bottom Right
  glVertex3f(-1.0f,-1.0f, 0.0f);		// Bottom Left	
  glEnd();					// we're done with the polygon
    
  glTranslatef(3.0f,0.0f,0.0f);		        // Move Right 3 Units
	
  // draw a square (quadrilateral)
  glBegin(GL_QUADS);				// start drawing a polygon (4 sided)
  glVertex3f(-1.0f, 1.0f, 0.0f);		// Top Left
  glVertex3f( 1.0f, 1.0f, 0.0f);		// Top Right
  glVertex3f( 1.0f,-1.0f, 0.0f);		// Bottom Right
  glVertex3f(-1.0f,-1.0f, 0.0f);		// Bottom Left	
  glEnd();					// done with the polygon
    
  // swap buffers to display, since we're double buffered.
  glutSwapBuffers();
}   
    
/* The function called whenever a key is pressed. */
void keyPressed(unsigned char key, int x, int y) 
{   
    /* avoid thrashing this procedure */
    usleep(100);
    
    /* If escape is pressed, kill everything. */
    if (key == ESCAPE) 
    { 
	/* shut down our window */
	glutDestroyWindow(window); 
	
	/* exit the program...normal termination. */
	//exit(0);                   
    }
}   
    
int main(int argc, char **argv) 
{   
  /* Initialize GLUT state - glut will take any command line arguments that pertain to it or 
     X Windows - look at its documentation at http://reality.sgi.com/mjk/spec3/spec3.html */  
  glutInit(&argc, argv);  
    
  /* Select type of Display mode:   
     Double buffer 
     RGBA color
     Alpha components supported 
     Depth buffer */  
  glutInitDisplayMode(GLUT_RGBA | GLUT_DOUBLE | GLUT_ALPHA | GLUT_DEPTH);  
    
  /* get a 640 x 480 window */
  glutInitWindowSize(640, 480);  
    
  /* the window starts at the upper left corner of the screen */
  glutInitWindowPosition(0, 0);  
    
  /* Open a window */  
  window = glutCreateWindow("Jeff Molofee's GL Code Tutorial ... NeHe '99");  
    
  /* Register the function to do all our OpenGL drawing. */
  glutDisplayFunc(&DrawGLScene);  
    
  /* Go fullscreen.  This is the soonest we could possibly go fullscreen. */
  glutFullScreen();
    
  /* Even if there are no events, redraw our gl scene. */
  glutIdleFunc(&DrawGLScene);
    
  /* Register the function called when our window is resized. */
  glutReshapeFunc(&ReSizeGLScene);
    
  /* Register the function called when the keyboard is pressed. */
  glutKeyboardFunc(&keyPressed);
    
  /* Initialize our window. */
  InitGL(640, 480);
    
  /* Start Event Processing Engine */  
  glutMainLoop();  
    
  return 1;
} 
```

Please guide me if im on the wrong track with the Libs that im using or there if there are errors in my compiling process.

Mitch :smile:

---

### Post by m87 on 2005-11-17
it's not that comfortable to use openGL directly, you should use something that wraps on openGL, like SDL or cairo/glitz. anyway i could do most 'abc' on openGL...

1) the nehe tutorial DOES work, but the glut bit is quite screwed up (or at least it was) and you should work around it to avoid errors
2) the API is C, not C++, you should use gcc therefore.

if you experience problems you can paste the errors!

marco

---

### Post by Burke on 2005-11-17
I hate to nitpick, but anything that is C is also C++ (99.9% of the time). Therefore, g++ will work perfectly well, and possibly better.

This is because C++ is a superset of C (C is a subset of C++), therefore C++ has all the features of C, plus many more. 

Other than that, I don't really have anything useful to contribute. I've never used OpenGL :)

---

### Post by ltmon on 2005-11-17
It's many orders of magnitude easier to program using an openGl engine, rather than direct to opengl itself.

Try ogre3d, irrlicht or crystal space for a couple of high-profile open source 3d engines.

L.

---

### Post by m87 on 2005-11-18
[QUOTE=Burke]I hate to nitpick, but anything that is C is also C++ (99.9% of the time). Therefore, g++ will work perfectly well, and possibly better.

This is because C++ is a superset of C (C is a subset of C++), therefore C++ has all the features of C, plus many more.[/QUOTE]

half truth, C++ is NOT a 100% superset of C... anyway I was just guessing, the guy didn't paste any error messages..

---

### Post by singamayya on 2007-02-17
> **m87 said:**
> half truth, C++ is NOT a 100% superset of C... anyway I was just guessing, the guy didn't paste any error messages..

Correct. The languages officially drift apart (i.e. are not compatible) starting from the C99 standard.

Use the right tool for the job -- don't force a square peg into a round hole! Use gcc for C and g++ for C++. Hint: we are not smarter than the GCC developers; if they thought g++ could handle C, then they would have deprecated gcc (made it a symlink to g++) a long time ago.

---

### Post by Wybiral on 2007-02-17
> It's many orders of magnitude easier to program using an openGl engine, rather than direct to opengl itself.

Try ogre3d, irrlicht or crystal space for a couple of high-profile open source 3d engines.

I find OpenGL exceedingly simple, even on it's own.

Anyway...

I've had no trouble compiling glut programs with "g++ program.cpp -lglut -lGLU -lGL" and I've never had to link to the X libraries.

But also... I HIGHLY recommend SDL over GLUT... It gives you much more freedom and also fits in well with SDL_image (a great library for loading images which can easily be used as OpenGL textures)

One more thing... Check out freeGLUT as a GLUT library, and MesaGL seems to be an identical alternative to the official OpenGL... So far I haven't noticed any inconsistencies and have programmed with both.

---

### Post by sdrubolo on 2007-02-18
Hi, 
I've been using openGL for one year, and in my spare time I keep programming. I hope that what I learnt will help you. About libraries, I don't know the different between those above. but if you wanna run openGL programs first you must have 3D acceleration enabled otherwise you wont succeed in watching smoothly your openGL programs. then you can install the openGL libraries, I think that those you listed above should be good (I checked and I also have those plus freeglut3). 
To compile your program, for example using C, you can do as follows "gcc -o yourFilename yourFilename.c -lglut". In your programs you don't need to add GL and GLU because those are included within the glut libraries. 
Finally, I think that using openGL is very nice because it helps you understand how graphics works, but you need a very sound background of vectors and its algebra otherwise you wont be able to do very interesting programs, especially lighting because for each surface you must calculate its own normal vector. 
Anyway, there are very useful books around and I suggest you to read one of them.
Bye.

---

### Post by UK-sHaDoW on 2007-02-18
> **m87 said:**
> it's not that comfortable to use openGL directly, you should use something that wraps on openGL, like SDL or cairo/glitz. anyway i could do most 'abc' on openGL...

1) the nehe tutorial DOES work, but the glut bit is quite screwed up (or at least it was) and you should work around it to avoid errors
2) the API is C, not C++, you should use gcc therefore.

if you experience problems you can paste the errors!

marco

I seriously doubt you could not use the openGL Library with c++. I do all the time

---

### Post by stv2007 on 2008-05-19
hi there is an easy way
see [http://www.ferdychristant.com/blog/articles/DOMM-72MPPE](http://www.ferdychristant.com/blog/articles/DOMM-72MPPE)
using eclipse
bye

---

### Post by qewrtyuiop on 2009-01-20
Is there any plain and simple way of programming in opengl without a wrapper?  I don't have much experience with opengl in C/++ but I've used it to some extent with JOGL (openGL port to JAVA) and I'd like to play with it in C++.  Is there any way to use it without a wrapper to dumb it all down?

---

### Post by Wybiral on 2009-01-20
> **qewrtyuiop said:**
> Is there any plain and simple way of programming in opengl without a wrapper?  I don't have much experience with opengl in C/++ but I've used it to some extent with JOGL (openGL port to JAVA) and I'd like to play with it in C++.  Is there any way to use it without a wrapper to dumb it all down?

Define "wrapper"?

---

### Post by qewrtyuiop on 2009-01-20
The SDL and GLUT libraries that were being described earlier.

---

### Post by Wybiral on 2009-01-20
SDL doesn't "wrap" anything, it just opens a window with OpenGL context for you (and lets you catch events from that window like mouse/key/exit). It doesn't affect the actual OpenGL code at all.

---

### Post by qewrtyuiop on 2009-01-21
Thanks for the clarification.  The idea I got was that it represented its own layer of code.

---

### Post by slavik on 2009-01-21
> **Wybiral said:**
> SDL doesn't "wrap" anything, it just opens a window with OpenGL context for you (and lets you catch events from that window like mouse/key/exit). It doesn't affect the actual OpenGL code at all.
Actually, there are somethings that have to be called different, I think it's related attributes, you have to call them through SDL (you just add SDL_ to the beginning of the function name).

There is no "official" OpenGL implementation for Linux, but Mesa follows the published standard, so you can consider it authoritative ... being an official implementation requires paying money to the OpenGL board which the developer doesn't have nor cares to acquire.

---


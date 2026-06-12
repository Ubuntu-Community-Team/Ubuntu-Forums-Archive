---
title: "Starting OpenGL help"
date: 2009-09-23
forum: Programming Talk
---

### Post by Xenomorph05 on 2009-09-23
I have been trying to use NetBeans 6.7.1, and Eclipse for making simple C++ OpenGL programs but it's not working. In class we use VisualStudio 2008 and any code from that class doesn't work when I try to use it in either compiler. 

I have tried to google for tutorials but they are very complicated. I can't just use the #includes for glut and stuff like in VS 2008? 

Also why does netbeans use 300Mb of RAM? It kills my computer since I only have 1Gb. 

Thanks for your time and I am frustrated that opengl isn't easier to use on Ubuntu then on windows.

I am having Netbeans math problems now... :(

---

### Post by scragar on 2009-09-23
It should be the same difficulty, you just need to make sure glut is used when compiling:
```
g++ -Iglut -lglut -o execute_me source.cpp
```

EDIT: the -I says use this include path, -l says load this library from the include path. This has to be done this way because of the way includes that are inside sub dir's work, VS would do this for you, and any good IDE will handle this as well, using the core tools however you must do this manually, since it's not always expected behaviour(and working for anything you want is better than being slightly easier 95% of the time).

---

### Post by Xenomorph05 on 2009-09-23
I would prefer to use an IDE vs command line but I did cd to the directory with the main.cpp and i tried to use
g++ -Iglut -lglut -o execute_me main.cpp but nothing happened at all.

---

### Post by scragar on 2009-09-23
No error messages or anything? Did you check for the file called execute_me in the directory? Did you try executing it?

---

### Post by Xenomorph05 on 2009-09-23
Cool, I didn't know I had to use the execute_me. hadn't seen that before. When I executed it the example I have been trying to use works, thanks for that! 

Does this mean I should skip using an IDE and just compile with command line?

---

### Post by scragar on 2009-09-23
For future ref the -o flag sets the output file name, so ```
-o execute_me
```saved the executable as execute_me, it's a good idea to name it something better for yourself. If the flag isn't specified you get a file called **a.out** which is a horrible naming convention imo.

It's completely up to you, IDEs save time and effort, but doing it by hand, gives you a better understanding of how it works.

---

### Post by Xenomorph05 on 2009-09-23
Why are the IDE so hard to set up though, Mono, Netbeans, eclipse, for c++. I see netbeans has a Java opengl pack but I can't run any opengl code from scratch with c++ in the IDE???

EDIT: If I completely removed my IDE and used command line then how does error handling work? Is there a flawless way to get set up to use openGL on ubuntu with IDE? Eclipse runs into build issues, mono gtkglare tutorials don't work anymore(that i tried).

---

### Post by scragar on 2009-09-23
Try geany, it's as simple as they come.

You'll want to go to the little drop down next to build and choose set includes and arguments, from there make sure to set the line up for compile like so:
```
g++ -Iglut -lglut -o "%e" "%f"
```
Which will take "foo.cpp" and spit out the executable "foo". You also can check warnings and such from here, which is very helpfull.
And it has single button compiling.

EDIT: when you get used to geany look into how to create a project, since then you'll be able to compile files with multiple includes without having to keep going to the main file files, since you don't need that now though I'll avoid confusing you.

---

### Post by Xenomorph05 on 2009-09-23
I installed Geany, pasted the code in, saved a new .cpp file and it compiles without error but will not execute. it says the 5: ./main: not found??

---

### Post by scragar on 2009-09-23
Always worked fine for me, can you post a screenshot of your compile and execute settings in the menu I told you about?(alt+print screen to snap a single window)

---

### Post by Xenomorph05 on 2009-09-23
I don't know how to make code or images appear in the thread. I can post a link to imageshack if that's alright?
EDIT: maybe this will work?
[[IMG]http://img101.imageshack.us/img101/2561/geanynotfound.th.jpg[/IMG]](http://img101.imageshack.us/i/geanynotfound.jpg/)

---

### Post by Can+~ on 2009-09-23
> Also why does netbeans use 300Mb of RAM? It kills my computer since I only have 1Gb.

I recommend you to use Eclipse, it's usually lighter and more responsive than Netbeans (currently using 90~100 MB), although you need to [download it from their page]("http://www.eclipse.org/downloads/"), not from the repository.

But for short snippets I also say "go with geany" or gedit.

> Why are the IDE so hard to set up though, Mono, Netbeans, eclipse, for c++. I see netbeans has a Java opengl pack but I can't run any opengl code from scratch with c++ in the IDE???

Because C and C++ are languages that require some knowledge on how to compile, there's no magic "fix it for me" button. In this case, you need to compile and specify directly which libraries need to be used as scargar pointed out. Probably your class has the libraries already set up to be used for the task.

Also, make sure you have freeglut3-dev and friends installed.

---

### Post by scragar on 2009-09-23
I meant this window.

---

### Post by Xenomorph05 on 2009-09-23
I have both eclipse from repository and the download from the site. The one from the site I have to go to the folder it extracted in. I have all of the opengl stuff from the synaptic package manager. 

Is there a tut that explains set up of opengl for any IDE that is 100% going to work?

Scargar: I don't know where that window is. I haven't seen it.

---

### Post by scragar on 2009-09-23
It's right where I said it was.

You want to make sure that the path used to execute the file matches the output file for compiling it. Use the command I posted a little while back in the compile line.

---

### Post by Xenomorph05 on 2009-09-23
sorry, thanks for the screen :) I found it now.

Compile: g++ -Wall -c "%f"
build:   g++ -Wall -o "%e" "%f"
execute: "./%e"

---

### Post by scragar on 2009-09-23
Yes, well, there's your problem. It's compiling it with **-c** which produces an output file rather than a compiled program(actually that's a good idea since it's slightly faster if you're testing for compile errors, or planning to use the same include a lot, but for you right now it's pretty useless).
Edit the build line to read:
```
g++ -Iglut -lglut -o "%e" "%f"
```And you should be able to click build, then compile to get your code working perfectly.

EDIT: For clarity I always used compile for single files and build for projects, but apparently that doesn't matter, go figure :p

---

### Post by Can+~ on 2009-09-23
```
sudo apt-get install freeglut3-dev
```

(From NeHe's)
[PHP]//
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
  glClearColor(0.0f, 0.0f, 0.0f, 0.0f);		// This Will Clear The Background Color To Black
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
	exit(0);                   
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
[/PHP]

```
gcc -lglut -lGL -lGLU test.c -o test
./test
```

For C++ it should be g++ instead of gcc.

---

### Post by Xenomorph05 on 2009-09-23
Scragar: That didn't let me build. I even tried the sample code Can+~ posted which I get an exit error at line 94... If I comment it out I still can't build. This is with geany and I tried command line. 

I don't understand what geany is telling me is wrong with it though.

I also already have the newest freeglut.

---

### Post by scragar on 2009-09-23
It's late for me(I'm up at 3am tomorrow), if you can post the error output and your code, along with what you've got for your compile line(again, just in case you've coppied it wrong or I've wrote it out wrong and messed up) and I'll take a look before bed, k?

---

### Post by elasolova on 2009-09-23
Do you know about nehe tutorials? They are very useful for beginners. They start from the beginning and build up. I tried to learn OpenGl from those some time ago. However, I gave up as I am not yet ready for OpenGl. It really requires experience.

---

### Post by Xenomorph05 on 2009-09-23
i used the code posted above, it errored at line 94 so i commented it out and it did actually execute and i saw a square and triangle but it was full screen and i tried to minimize it and my whole screen went black lol now my laptop is frozen haha...

Thanks for your time and help, i'll keep fighting with it.

---

### Post by Can+~ on 2009-09-23
Line 94 doesn't produce an error, it's just a warning. It just needs #include <stdlib.h> for the exit() function.

---

### Post by Xenomorph05 on 2009-09-23
i'll try the include when i get home and turn my laptop back on. i will try the NeHe tonight! I have been trying to use the videotutorialsrock.com stuff but it's not helping me much.

---

### Post by Xenomorph05 on 2009-09-23
Thanks! It seems I will be using Geany for my OpenGL needs! I do wish that the other compilers were better set up. 

using the ```
g++ -Iglut -lglut -o "%e" "%f"
``` is the main thing that I need to change, which I don't mind. 

Thanks again!

---

### Post by Xenomorph05 on 2009-11-02
Hey, Sorry I didn't want to start a new thread. This is related anyway to the problem I had before, kindof..

In Netbeans on Ubuntu how do you use sin, cos, tan? Math.h doesn't work. I followed two guides that said to add -lm and mathematics to the linker but that doesn't work. 

I get this error: sin was not declared in this scope

do I need to declare sin in Netbeans?

Thanks

---

### Post by Can+~ on 2009-11-02
> I get this error: sin was not declared in this scope

do I need to declare sin in Netbeans?

You will probably have to edit the linking process to add the "-lm" flag there. I don't use Netbeans, so I can't help you with that.

---

### Post by Xenomorph05 on 2009-11-02
I right clicked the project, properties, selected linker, clicked a button to add to libraries, add standard and added Mathematics. I also chose to Add Option and other option then added -lm. Neither have fixed my sin, cos problem.

Well anyway I just checked to see if Netbeans has a math include and it does. math.h rather then the Math.h I was trying to use. haha silly me. 

I am going to try to import some 3D models and sound so I will post if I run into problems. I will be very happy if I can program 3D games with Ubuntu. :D

---


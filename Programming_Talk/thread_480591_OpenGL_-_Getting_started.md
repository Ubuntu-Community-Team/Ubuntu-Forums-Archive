---
title: "OpenGL - Getting started"
date: 2007-06-21
forum: Programming Talk
---

### Post by batrick on 2007-06-21
Hello all,

I'm desperately trying to get >something< compiled and running for OpenGL (in C). I've installed the right packages I need: freeglut3 and freeglut3-dev.

It took a while but I got this compiled:

```

#include <GL/glut.h>

#define window_width  640
#define window_height 480

// Main loop
void main_loop_function()
{
  // Z angle
  static float angle;
  // Clear color (screen) 
  // And depth (used internally to block obstructed objects)
  glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
  // Load identity matrix
  glLoadIdentity();
  // Multiply in translation matrix
  glTranslatef(0,0, -10);
  // Multiply in rotation matrix
  glRotatef(angle, 0, 0, 1);
  // Render colored quad
  glBegin(GL_QUADS);
  glColor3ub(255, 000, 000); glVertex2f(-1,  1);
  glColor3ub(000, 255, 000); glVertex2f( 1,  1);
  glColor3ub(000, 000, 255); glVertex2f( 1, -1);
  glColor3ub(255, 255, 000); glVertex2f(-1, -1);
  glEnd();
  // Swap buffers (color buffers, makes previous render visible)
  glutSwapBuffers();
  // Increase angle to rotate
  angle+=0.25;
}

// Initialze OpenGL perspective matrix
void GL_Setup(int width, int height)
{
  glViewport( 0, 0, width, height );
  glMatrixMode( GL_PROJECTION );
  glEnable( GL_DEPTH_TEST );
  gluPerspective( 45, (float)width/height, .1, 100 );
  glMatrixMode( GL_MODELVIEW );
}

// Initialize GLUT and start main loop
int main(int argc, char** argv) {
  glutInit(&argc, argv);
  glutInitWindowSize(window_width, window_height);
  glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE);
  glutCreateWindow("GLUT Example!!!");
  glutIdleFunc(main_loop_function);
  GL_Setup(window_width, window_height);
  glutMainLoop();
}

```

This program compiled fine. I compiled it with:

gcc hello.c -lglut -lX11

It still compiles without X11, so I don't think it's necessary.

My problem is when I try to run the program I get:

$ a.out
freeglut (a.out): OpenGL GLX extension not supported by display ':0.0'

This I'm running (naturally) in the terminal, which I believe may be the problem. How do I get this to work? I don't want to use an IDE, just a terminal.

Thanks for any help!

---

### Post by moma on 2007-06-21
[COLOR="Red"]> OpenGL GLX extension not supported by display ':0.0'[/COLOR]

I think you must do this:
You must activate support for OpenGL. It means that you need to install a proper display driver for your graphic card. It's guite easy to do so.  

Do as instructed in this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Or run Step 6) of [this guide... ]("http://www.futuredesktop.org")
--------------------
If you encounter problems, report 
* What version of Ubuntu you run.
* The type of graphic card in question. This command will tell you that
$ [COLOR="SeaGreen"]lspci  | grep -i vga[/COLOR]

--------------------
BTW:  Your code is missing a glutDisplayFunc'tion.
Remove the angle calculation away from main_loop_function() to idle_function() like this:

// Z angle   (this is global now)
float angle;

void idle_function()
{
 // Increase angle to rotate
  angle+=0.25;

  glutPostRedisplay();
}

And add this to the main() function.

  glutIdleFunc(idle_function);
  glutDisplayFunc(main_loop_function);  //  <-- main_loop_function is a bad name. Rename it ;-)

---

### Post by batrick on 2007-06-21
I've already got the correct nvidia graphics driver installed. : (

---

### Post by batrick on 2007-06-21
> **moma said:**
> [COLOR="Red"]BTW:  Your code is missing a glutDisplayFunc'tion.
Remove the angle calculation away from main_loop_function() to idle_function() like this:

// Z angle   (this is global now)
float angle;

void idle_function()
{
 // Increase angle to rotate
  angle+=0.25;

  glutPostRedisplay();
}

And add this to the main() function.

  glutIdleFunc(idle_function);
  glutDisplayFunc(main_loop_function);  //  <-- main_loop_function is a bad name. Rename it ;-)

I did what you put, still the same error. I didn't make the code, I admit it looks pretty gross in a few places :) I just wanted something >working<.

---

### Post by kknd on 2007-06-21
It compiles here.

You must turn off XGL (AiGLX goes well)

---

### Post by batrick on 2007-06-22
> **kknd said:**
> It compiles here.

You must turn off XGL (AiGLX goes well)

It compiles for me as well. But I get an error message when I try to run it as outlined in my OP. If your second comment refers to fixing that, I don't think I understand, could you elaborate please?

---

### Post by moma on 2007-06-23
Allo,allo

Agree. Your code is good enough to start with. Do not wory about it,  BUT 

I still think that 
you must activate support for OpenGL. It means that you need to install a proper display driver for your graphic card.  It's guite easy to do so.  It will also fix your /etc/X11/xorg.conf file and load the glx module.

Do as instructed in this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Or run through step 6) of this [http://www.futuredesktop.org/](http://www.futuredesktop.org/) manual.
---------------------------------

BTW:  _**After**_ you've fixed the main problem.
[http://nehe.gamedev.net/](http://nehe.gamedev.net/) site has good OpenGL lessons.
Read the "[COLOR="SeaGreen"]Let's have an example[/COLOR]" part of this message: [http://ubuntuforums.org/showthread.php?p=2868563#post2868563](http://ubuntuforums.org/showthread.php?p=2868563#post2868563)

---

### Post by skullmunky on 2007-06-26
moma's probably correct.  try other, existing opengl programs to tell if opengl is working, first.  see what glxgears does.  if it dies with the same error, you have a problem with your graphics driver installation.

---

### Post by Mickeysofine1972 on 2007-06-27
Also,

Try the tutorials on the Ubuntu Games Developers Wiki ([http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com))

Mike

---


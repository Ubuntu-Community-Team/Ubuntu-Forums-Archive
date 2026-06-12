---
title: "OpenGL"
date: 2010-07-09
forum: Programming Talk
---

### Post by preeti_patil on 2010-07-09
Hi,
 
I am trying to compile a oepngl program. Below is the error i am getting.
 
[SIZE=3][FONT=Consolas]/usr/bin/ld: cannot find -lglut[/FONT][/SIZE]
[FONT=Calibri]collect2: ld returned 1 exit status[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]Kindly help if i am suppose to install any libraries or linking has to be done.[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]Thanks & Regards,[/FONT]
[FONT=Calibri]Preeti [/FONT]

---

### Post by pbrane on 2010-07-09
Looks like you need to install glut. I have freeglut3, freeglut3-dev, and libglut3-dev installed on my machine. They are in the repos.

---

### Post by preeti_patil on 2010-07-09
thanks pbrane
 
can you please send me link where i can find these libraries and how to install them on ubutu platform
 
thanks & regards,
preeti

---

### Post by efikkan on 2010-07-09
Just type the following in terminal:
```
sudo apt-get install freeglut3 freeglut3-dev libglut3-dev 

```
Or find them manually in Synaptic.

---

### Post by preeti_patil on 2010-07-10
I have installed the mentioned libraries (freegult-2.6.0), still i am getting same errors. Do i have to compile the opengl applications with specific command??

thanks & regards,
preeti

---

### Post by kahumba on 2010-07-10
Add also -lGLU and -lGL.

---

### Post by preeti_patil on 2010-07-10
thanks for the reply i was able to successfully compile the program. Now got error saying

c:353: undefined reference to `gluPerspective'
c:226: undefined reference to `gluLookAt'

I think these functions are depreciated, if so can anyone suggest me which functions to replace these.

Thanks & Regards,
Preeti

---

### Post by crazyfuturamanoob on 2010-07-10
They're not depreciated as I know. I have been using gluPerspective in 90% of my OpenGL apps. Did you link with GLU (by passing -lGLU to gcc)?

---

### Post by kahumba on 2010-07-10
If you want to solve your issue quicker just post your source code and how you're compiling it so people will reproduce it and tell you what exactly you need to know, without having to guess as we do now.

---

### Post by efikkan on 2010-07-10
First check if you have included the required header files in your source code.
Then check if you parse the correct arguments to GCC.
And then go to /usr/include/GL/ and check if you got the correct header file.

---

### Post by preeti_patil on 2010-07-12
#include<GL/glut.h> 
 
#include<stdlib.h> 
 
#include<math.h> 
 
const float DEG2RAD = 3.14159/180; 
 
static int shoulder = 0, elbow = 0,gripper=0,shldf=0; 
 
//GLfloat position[]={0.0,0.0,5.0,1.0}; 
 
void init()  
 
{ 
 
   glClearColor (1.0, 1.0, 1.0, 0.0); 
 
   glShadeModel (GL_SMOOTH); 
 
   //glEnable(GL_LIGHTING);     
 
   //glEnable(GL_LIGHT0); 
 
   //glLightfv(GL_LIGHT0,GL_POSITION,position); 
 
   glEnable(GL_DEPTH_TEST); 
 
} 
 
 
 
 
 
void keyboard (unsigned char key, int x, int y) 
 
{ 
 
   switch (key)  
 
   { 
 
      case 's': 
 
         shoulder = (shoulder + 2) % 360;        //Shoulder Motion 
 
         glutPostRedisplay(); 
 
         break; 
 
      case 'S': 
 
         shoulder = (shoulder - 2) % 360;        //Shoulder Motion 
 
         glutPostRedisplay(); 
 
         break; 
 
      case 'e': 
 
         elbow = (elbow + 2) % 90;                //Elbow Motion 
 
         glutPostRedisplay(); 
 
         break; 
 
      case 'E': 
 
         elbow = (elbow - 2) % 90;                //Elbow Motion 
 
         glutPostRedisplay(); 
 
         break; 
 
      case 'g': 
 
          gripper=(gripper+2)%360;                //Gripper Motion 
 
          glutPostRedisplay(); 
 
          break; 
 
      case 'G': 
 
          gripper=(gripper-2)%360;                //Gripper Motion 
 
          glutPostRedisplay(); 
 
          break; 
 
      case 'f': 
 
          shldf=(shldf+2)%45;                    //Shoulder to-fro motion 
 
          glutPostRedisplay(); 
 
          break; 
 
      case 'F': 
 
          shldf=(shldf-2)%75;                    //Shoulder to-fro Motion 
 
          glutPostRedisplay(); 
 
          break; 
 
      case 27: 
 
         exit(0); 
 
         break; 
 
      default: 
 
         break; 
 
   } 
 
} 
 
 
 
 
 
void base_arm() 
 
{ 
 
   glPushMatrix(); 
 
 
 
   glScalef (1.0,0.1,0.4); 
 
   glColor3f(0.0,.0,0.0); 
 
   glutSolidCube (1.0);   //Connecting cube 
 
   glPopMatrix(); 
 
   glPushMatrix(); 
 
 
   glTranslatef(0.0,-0.6,0.0); 
 
   glColor3f(0.0,.0,0.0); 
 
   glScalef(1.0,0.1,0.4); 
 
   glutSolidCube(1.0);    //Connecting Cube 
 
   glPopMatrix(); 
 
   glPushMatrix(); 
 
   glTranslatef(0.0,0.6,0.0); 
 
   glScalef(1.0,0.1,0.4); 
 
   glColor3f(0.0,.0,0.0); 
 
   glutSolidCube(1.0);    //Connecting Cube 
 
   glPopMatrix(); 
 
   glPushMatrix(); 
 
   glTranslatef(-0.5,0.0,0.0); 
 
   glScalef(0.4,2.0,0.4); 
 
   glColor3f(0.4,.4,0.4); 
 
   glutSolidCube(1.0);    //Side Long Cube 
 
   glPopMatrix(); 
 
   glPushMatrix(); 
 
   glTranslatef(0.5,0.0,0.0); 
 
   glScalef(0.4,2.0,0.4); 
 
   glColor3f(0.4,.4,0.4); 
 
   glutSolidCube(1.0);    //Side Long Cube 
 
   glPopMatrix(); 
 
} 
 
 
 
  
 
void drawCircle(float radius)    //Code to draw semi-circle; 360 limit in for loop draws circle,but i need filled one
 
{ 
 
   glBegin(GL_TRIANGLE_FAN); 
 
    
 
   for (int i=0; i<360; i++) 
 
   { 
 
      float degInRad = i*DEG2RAD; 
 
      glVertex2f(cos(degInRad)*radius,sin(degInRad)*radius); 
 
   } 
 
  
 
   glEnd(); 
 
} 
 
 
 
void drawSemiCircle(float radius)            //Code to draw semi-circle; 360 limit in for loop draws circle,but i need filled one 
 
{ 
 
   glBegin(GL_TRIANGLE_FAN); 
 
    
 
   for (int i=0; i<180; i++) 
 
   { 
 
      float degInRad = i*DEG2RAD; 
 
      glVertex2f(cos(degInRad)*radius,sin(degInRad)*radius); 
 
   } 
 
  
 
   glEnd(); 
 
} 
 
 
 
void robotarm() 
 
{ 
 
   glPushMatrix(); 
 
   glTranslatef(0.0,-1.4,0.0); 
 
   glPushMatrix(); 
 
   glColor3f(0.0,.0,0.0); 
 
   glRotatef(90.0,1.0,0.0,0.0); 
 
   glTranslatef(0.0,0.0,-0.3); 
 
   drawCircle(1.0); 
 
   glPopMatrix(); 
 
   glColor3f(0.0,.0,0.0); 
 
   glTranslatef(0.0,0.0,-0.5); 
 
   glScalef(3.0,0.5,3.0); 
 
   glutSolidCube(1.0);                                //Fixed Base 
 
   glTranslatef(0.0,-1.0,-0.5); 
 
   glScalef(2.0,0.5,2.0); 
 
   glColor3f(0.0,0.0,0.0); 
 
   glutSolidCube(1.0); 
 
   glPopMatrix(); 
 
   glPushMatrix(); 
 
   glColor3f(1.0,0.0,0.0); 
 
   glRotatef((GLfloat) shoulder, 0.0, 1.0, 0.0);    //360deg motion;  
 
   glPushMatrix(); 
 
   glTranslatef(-0.7,-1.1,0.0); 
 
   glRotatef(90.0,0.0,1.0,0.0); 
 
   glColor3f(0.0,0.0,1.0); 
 
   drawSemiCircle(0.3); 
 
   glPopMatrix(); 
 
   glPushMatrix(); 
 
   glTranslatef(0.7,-1.1,0.0); 
 
   glRotatef(90.0,0.0,1.0,0.0); 
 
   glColor3f(0.0,0.0,1.0); 
 
   drawSemiCircle(0.3); 
 
   glPopMatrix(); 
 
   glPushMatrix(); 
 
   glTranslatef(0.0,-1.0,0.0); 
 
   glRotatef(shldf,1.0,0.0,0.0);                    //180deg frnt-bck motion 
 
   glTranslatef(0.0,1.0,0.0); 
 
   glPushMatrix(); 
 
    
 
   base_arm();                                        //Shoulder to elbow 
 
   glPushMatrix(); 
 
   glTranslatef(-0.71,1.0,0.0); 
 
   glRotatef(90.0,0.0,1.0,0.0); 
 
   glColor3f(0.0,0.0,1.0); 
 
   drawCircle(0.2); 
 
   glPopMatrix(); 
 
   glPushMatrix(); 
 
   glTranslatef(0.71,1.0,0.0); 
 
   glRotatef(90.0,0.0,1.0,0.0); 
 
   glColor3f(0.0,0.0,1.0); 
 
   drawCircle(0.2); 
 
   glPopMatrix(); 
 
   glTranslatef(0.0,1.0,0.0); 
 
   glRotatef(90.0,1.0,0.0,0.0); 
 
   glTranslatef(0.0,1.0,0.0); 
 
   glTranslatef(0.0,-1.0,0.0); 
 
   glRotatef((GLfloat) elbow,1.0,0.0,0.0);            //Elbow rotation 
 
   glTranslatef(0.0,1.0,0.0); 
 
   base_arm();                                        //elbow to Gripper 
 
   glPushMatrix(); 
 
   glColor3f(.7,0.7,.7); 
 
   glTranslatef(0.0,1.2,0.0); 
 
   glRotatef(90.0,1.0,0.0,0.0); 
 
   glScalef(1.5,0.5,0.4); 
 
   glRotatef(gripper,0.0,0.0,1.0); 
 
   glutSolidCube(1.0);                                //Gripper 
 
   glPopMatrix(); 
 
   glPopMatrix(); 
 
   glPopMatrix(); 
 
   glPopMatrix(); 
 
} 
 
 
 
 
 
void display(void) 
 
{ 
 
   glClear (GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT); 
 
   glPushMatrix(); 
 
   glScalef(0.8,0.8,0.8);                            //To Show entire robo arm within the window 
 
   robotarm(); 
 
   glPopMatrix(); 
 
   glutSwapBuffers(); 
 
} 
 
 
 
void reshape (int w, int h) 
 
{ 
 
   GLint xc=100,yc=450,r=10; 
 
   glViewport (0, 0, (GLsizei) w, (GLsizei) h);  
 
   glMatrixMode (GL_PROJECTION); 
 
   glLoadIdentity (); 
 
   gluPerspective(65.0, (GLfloat) w/(GLfloat) h,1.0, 20.0); 
 
   glMatrixMode(GL_MODELVIEW); 
 
   glLoadIdentity(); 
 
   glTranslatef (0.0, 0.0, -5.0); 
 
} 
 
 
 
int main(int argc, char** argv) 
 
{ 
 
   glutInit(&argc, argv); 
 
   glutInitDisplayMode (GLUT_DOUBLE | GLUT_RGB); 
 
   glutInitWindowSize (600, 600);  
 
   glutInitWindowPosition (0,0); 
 
   glutCreateWindow ("Robot Arm Simulation"); 
 
   init(); 
 
   glutDisplayFunc(display);  
 
   glutReshapeFunc(reshape); 
 
   glutKeyboardFunc(keyboard); 
 
   glutMainLoop(); 
 
   return 0; 
 
}

This is the code i am trying to compile and below are the error i am getting.
shapes-shapes.o: In function `reshape':
/home/satyam/Poonam/src/freeglut-2.6.0/progs/demos/shapes/shapes.c:428: undefined reference to `gluPerspective'
collect2: ld returned 1 exit status
make: *** [shapes] Error 1


Thanks & Regards,
Preeti

---

### Post by preeti_patil on 2010-07-12
/* $Id: robot.c,v 1.3 2005/03/09 13:53:46 aholkner Exp $
 *
 * Robot arm demo framework for Interactive 3D Graphics and Animation
 *
 * Alex Holkner
 * [http://yallara.cs.rmit.edu.au/~aholkner](http://yallara.cs.rmit.edu.au/~aholkner)
 *
 * See below for hints on how to start off your project using this framework.
 */

/*
 * Copyright (c) 1993-1997, Silicon Graphics, Inc.
 * ALL RIGHTS RESERVED
 * Permission to use, copy, modify, and distribute this software for
 * any purpose and without fee is hereby granted, provided that the above
 * copyright notice appear in all copies and that both the copyright notice
 * and this permission notice appear in supporting documentation, and that
 * the name of Silicon Graphics, Inc. not be used in advertising
 * or publicity pertaining to distribution of the software without specific,
 * written prior permission.
 *
 * THE MATERIAL EMBODIED ON THIS SOFTWARE IS PROVIDED TO YOU "AS-IS"
 * AND WITHOUT WARRANTY OF ANY KIND, EXPRESS, IMPLIED OR OTHERWISE,
 * INCLUDING WITHOUT LIMITATION, ANY WARRANTY OF MERCHANTABILITY OR
 * FITNESS FOR A PARTICULAR PURPOSE.  IN NO EVENT SHALL SILICON
 * GRAPHICS, INC.  BE LIABLE TO YOU OR ANYONE ELSE FOR ANY DIRECT,
 * SPECIAL, INCIDENTAL, INDIRECT OR CONSEQUENTIAL DAMAGES OF ANY
 * KIND, OR ANY DAMAGES WHATSOEVER, INCLUDING WITHOUT LIMITATION,
 * LOSS OF PROFIT, LOSS OF USE, SAVINGS OR REVENUE, OR THE CLAIMS OF
 * THIRD PARTIES, WHETHER OR NOT SILICON GRAPHICS, INC.  HAS BEEN
 * ADVISED OF THE POSSIBILITY OF SUCH LOSS, HOWEVER CAUSED AND ON
 * ANY THEORY OF LIABILITY, ARISING OUT OF OR IN CONNECTION WITH THE
 * POSSESSION, USE OR PERFORMANCE OF THIS SOFTWARE.
 *
 * US Government Users Restricted Rights
 * Use, duplication, or disclosure by the Government is subject to
 * restrictions set forth in FAR 52.227.19(c)(2) or subparagraph
 * (c)(1)(ii) of the Rights in Technical Data and Computer Software
 * clause at DFARS 252.227-7013 and/or in similar or successor
 * clauses in the FAR or the DOD or NASA FAR Supplement.
 * Unpublished-- rights reserved under the copyright laws of the
 * United States.  Contractor/manufacturer is Silicon Graphics,
 * Inc., 2011 N.  Shoreline Blvd., Mountain View, CA 94039-7311.
 *
 * OpenGL(R) is a registered trademark of Silicon Graphics, Inc.
 */

/*
 * robot.c
 * This program shows how to composite modeling transformations
 * to draw translated and rotated hierarchical models.
 * Interaction:  pressing the s and e keys (shoulder and elbow)
 * alters the rotation of the robot arm.  Hold down shift while pressing
 * S and E to rotate in the opposite direction.
 */

/* Default values to compile on Linux if no config.os/Makefile is used
 */
#ifndef GL_HEADER
#  define GL_HEADER   <GL/gl.h>
#  define GLU_HEADER  <GL/glu.h>
#  define GLUT_HEADER <GL/glut.h>
#endif

/* The following lines should be present in ALL of your source files;
 * rather than including the GL, GLU and GLUT headers directly we use
 * constants which are defined by the Makefile.  This means the same code
 * can be compiled without change on Linux, Windows and Mac.
 */
#ifdef WIN32
#  include <windows.h>
#endif
#include GL_HEADER
#include GLU_HEADER
#include GLUT_HEADER

#include <stdlib.h>

/* Initial positions of the shoulder and elbow joints, in degrees.
 * This is a simple example and uses global constants, however in
 * a larger project they should be members of a (non-static) struct.
 */
static int shoulder = 0, elbow = 0;

/* The init function is called once after GLUT is initailised but before
 * any drawing happens.  We set the background color to 0,0,0 (black)
 * and the shading model to FLAT
 */
void init(void)
{
   glClearColor(0.0, 0.0, 0.0, 0.0);
   glShadeModel(GL_FLAT);
}

/* The display function is called by GLUT to draw a single frame.  It can
 * called repeatedly; potentially hundreds of times a second; but in this
 * demo it is only called when a key is pressed and at the start of the
 * application.
 */
void display(void)
{
   /* Clear the frame; that is, erase anything that was drawn in previous
    * frames. */
   glClear(GL_COLOR_BUFFER_BIT);

   /* The push/pop calls save and recall the state of the modelview
    * matrix.  I have indented the code between these calls so you can
    * see how they pair up.
    */
   glPushMatrix();
     /* Translate the modelview matrix -1 units on the x-axis */
     glTranslatef(-1.0, 0.0, 0.0);
     /* Rotate the modelview matrix around the z-axis by the shoulder-angle */
     glRotatef((GLfloat) shoulder, 0.0, 0.0, 1.0);
     /* Translate the modelview matrix +1 units on the x-axis; i.e.
      * move to the mid-point of the upper-arm */
     glTranslatef(1.0, 0.0, 0.0);
     glPushMatrix();
       /* Draw a cube (the upper-arm) of dimensions 2.0 x 0.4 x 1.0 centered
        * around the origin.  We pushed the matrix here so the scale does not
        * affect any later operations. */
       glScalef(2.0, 0.4, 1.0);
       glutWireCube(1.0);
     glPopMatrix();

     /* Translate the modelview matrix +1 units along the x-axis; i.e.
      * move the the end of the upper-arm (the elbow) */
     glTranslatef(1.0, 0.0, 0.0);
     /* Rotate the modelview matrix around the z-axis by the elbow angle */
     glRotatef((GLfloat) elbow, 0.0, 0.0, 1.0);
     /* Translate the modelview matrix +1 units along the x-axis; i.e.
      * move to the half-way point of the lower-arm */
     glTranslatef (1.0, 0.0, 0.0);
     glPushMatrix();
       /* Draw a cube of dimensions 2.0 x 0.4 x 1.0 centered around the
        * origin. */
       glScalef (2.0, 0.4, 1.0);
       glutWireCube (1.0);
     glPopMatrix();

   glPopMatrix();

   /* This should always be the final call for the display function; it tells
    * GLUT that we have finished drawing this frame, and it will make it
    * visible on-screen. */
   glutSwapBuffers();
}

/* The reshape function is called by GLUT when the program starts and
 * also when the window is resized.  It defines the size of the viewport
 * (how much is visible), the field-of-view and near/far clipping planes.
 *
 * w  -- the new width of the window, in pixels
 * h  -- the new height of the window, in pixels
 */
void reshape (int w, int h)
{
   /* Set the viewport to be the same size as the window. */
   glViewport(0, 0, (GLsizei) w, (GLsizei) h);

   /* Tell OpenGL we want to modify the projection matrix instead of the
    * modelview matrix */
   glMatrixMode(GL_PROJECTION);
   /* Clear the old projection matrix */
   glLoadIdentity();
   /* Use GLU to create the projection matrix (if you do this without
    * GLU the mathematics can get a bit hairy).  The parameters are,
    * in order:
    *   65.0  -- Field of vision
    *   w/h   -- Aspect ratio
    *   1.0   -- Near clipping plane distance
    *   20.0  -- Far clipping plane distance
    */
   gluPerspective(65.0, (GLfloat) w/(GLfloat) h, 1.0, 20.0);

   /* Resume modifying the modelview matrix */
   glMatrixMode(GL_MODELVIEW);
   /* Clear the old modelview matrix -- we are now at the world origin */
   glLoadIdentity();
   /* Translate the modelview matrix -5 units on the z-axis; i.e. move the
    * camera back (out of the screen) 5 units */
   glTranslatef(0.0, 0.0, -5.0);
}

/* The keyboard function is called by GLUT every time a key is pressed,
 * or if a key is held down, the function is called repeatedly several
 * times a second.  The parameters are:
 *   key  -- The character that was pressed
 *   x, y -- The position of the mouse when the key was pressed
 */
void keyboard (unsigned char key, int x, int y)
{
   /* Note that we don't draw anything in this function.  Even though
    * the arm may have moved, all we do is update the global variables
    * indicating the angle of each joint; the arm will be redrawn the next
    * time the display function is called.  We do not call the display
    * function directly, it is important that GLUT calls it when everything
    * is ready.  Instead, the glutPostRedisplay function tells GLUT to
    * call display() as soon as possible.
    */
   switch (key) {
      /* For the 's' and 'e' keys, increment the shoulder and elbow
       * angles, respectively.  'S' and 'E' decrement instead.  The
       * angles are added modulo 360 (% 360) so that the angle is between
       * 0 and 365
       */
      case 's':
         shoulder = (shoulder + 5) % 360;
         glutPostRedisplay();
         break;
      case 'S':
         shoulder = (shoulder - 5) % 360;
         glutPostRedisplay();
         break;
      case 'e':
         elbow = (elbow + 5) % 360;
         glutPostRedisplay();
         break;
      case 'E':
         elbow = (elbow - 5) % 360;
         glutPostRedisplay();
         break;

      /* The ASCII code for ESC (escape key) is 27.  You can look up this
       * and other non-alphanumeric keys easily enough on the web.
       */
      case 27:
         exit(0);
         break;

      /* If any other key is pressed, ignore it */
      default:
         break;
   }
}

/* The main entry point of the program. */
int main(int argc, char** argv)
{
   /* We don't use any of the command-line arguments (argc and argv),
    * but we pass them to GLUT when we call init.  This means users can
    * enter any GLUT options (e.g. to select another display) to our program
    * and it will interpret them. */
   glutInit(&argc, argv);

   /* Set the options for OpenGL.  Descriptions:
    *  GLUT_DOUBLE  -- Use a separate back-buffer; this uses up more
    *                  video memory but prevents flicker
    *  GLUT_RGB     -- Specify each buffer has 24-bit color (8 bits for
    *                  each of red, green and blue).
    *  GLUT_DEPTH   -- Request a depth buffer in addition to the color
    *                  buffers. (not used in this demo)
    */
   glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB);

   /* Specify a default opening window size and position, in pixels */
   glutInitWindowSize(500, 500);
   glutInitWindowPosition(100, 100);

   /* Tell GLUT to create and display the window, with the given title */
   glutCreateWindow("Robot Arm Demo");

   /* Call our own init function to set up the background color and shading
    * model. */
   init ();

   /* Tell GLUT where each of our functions are.  We are passing in the name
    * of each function, which it will then call as required. */
   glutDisplayFunc(display);
   glutReshapeFunc(reshape);
   glutKeyboardFunc(keyboard);

   /* All initialisation is finished, tell GLUT to run the application forever
    * (or until we tell it to quit) */
   glutMainLoop();

   return 0;
}

Hi sir/mam,
Actually i am working for open source code of robot to move the arm of robot above is the code for that i able to compile the code   but getting error as bellow
shapes-shapes.o: In function `reshape':
/home/satyam/Poonam/src/freeglut-2.6.0/progs/demos/shapes/shapes.c:174: undefined reference to `gluPerspective'
collect2: ld returned 1 exit status
make: *** [shapes] Error 1


I replace gluPrespective() with glfrustum() this function but nothing is appearing

Thanks
Poonam

---

### Post by preeti_patil on 2010-07-13
Hi ,

Thank you for reply
I able run the code .
I m creating simulator of robotic arm getting so many .
The code in C# i trying  to convert in C programing the reference of code i taken from opengl.
please help me on that.
I am attaching code 


thank ,

---

### Post by preeti_patil on 2010-07-13
a

---


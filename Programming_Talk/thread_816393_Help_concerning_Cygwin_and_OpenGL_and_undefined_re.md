---
title: "Help concerning Cygwin and OpenGL and undefined references"
date: 2008-06-02
forum: Programming Talk
---

### Post by boboclock367 on 2008-06-02
Ok, so this is my first thread here and I am pretty new to programming.  So I worked on a linux machine for the better half of the year in my computer science class. I installed Cygwin with everything in it onto my laptop because I wanted to program.  However, I am having a problem with OpenGL and C++. I know the code should work but something is wrong with my accessing of libraries.   

The exact problem I get when compiling this is

/cygdrive/c/DOCUME~1/GEORGE~1/LOCALS~1/Temp/ccNGRZt6.o: In function `_Z7displayv':
/home/George Arceneaux/pacman/proto-game.cpp:22: undefined reference to `_glClear@4'
/home/George Arceneaux/pacman/proto-game.cpp:25: undefined reference to `_glColor3f@12'
/home/George Arceneaux/pacman/proto-game.cpp:26: undefined reference to `_glBegin@4'
/home/George Arceneaux/pacman/proto-game.cpp:27: undefined reference to `_glVertex2f@8'
/home/George Arceneaux/pacman/proto-game.cpp:28: undefined reference to `_glVertex2f@8'
/home/George Arceneaux/pacman/proto-game.cpp:29: undefined reference to `_glVertex2f@8'
/home/George Arceneaux/pacman/proto-game.cpp:30: undefined reference to `_glVertex2f@8'
/home/George Arceneaux/pacman/proto-game.cpp:31: undefined reference to `_glVertex2f@8'
/cygdrive/c/DOCUME~1/GEORGE~1/LOCALS~1/Temp/ccNGRZt6.o:/home/George Arceneaux/pacman/proto-game.cpp:32: more undefined references to `_glVertex2f@8' follow
/cygdrive/c/DOCUME~1/GEORGE~1/LOCALS~1/Temp/ccNGRZt6.o: In function `_Z7displayv':
/home/George Arceneaux/pacman/proto-game.cpp:39: undefined reference to `_glEnd@0'
/home/George Arceneaux/pacman/proto-game.cpp:55: undefined reference to `_glFlush@0'
/cygdrive/c/DOCUME~1/GEORGE~1/LOCALS~1/Temp/ccNGRZt6.o: In function `_Z7reshapeii':
/home/George Arceneaux/pacman/proto-game.cpp:102: undefined reference to `_glViewport@16'
/home/George Arceneaux/pacman/proto-game.cpp:104: undefined reference to `_glMatrixMode@4'
/home/George Arceneaux/pacman/proto-game.cpp:105: undefined reference to `_glLoadIdentity@0'
/home/George Arceneaux/pacman/proto-game.cpp:106: undefined reference to `_glOrtho@48'
/cygdrive/c/DOCUME~1/GEORGE~1/LOCALS~1/Temp/ccNGRZt6.o: In function `_Z4initv':
/home/George Arceneaux/pacman/proto-game.cpp:113: undefined reference to `_glClearColor@16'
/home/George Arceneaux/pacman/proto-game.cpp:114: undefined reference to `_glClear@4'
/home/George Arceneaux/pacman/proto-game.cpp:117: undefined reference to `_glMatrixMode@4'
/home/George Arceneaux/pacman/proto-game.cpp:118: undefined reference to `_glLoadIdentity@0'
/home/George Arceneaux/pacman/proto-game.cpp:119: undefined reference to `_glOrtho@48'
/home/George Arceneaux/pacman/proto-game.cpp:123: undefined reference to `_glPointSize@4'
/home/George Arceneaux/pacman/proto-game.cpp:124: undefined reference to `_glLineWidth@4'
/home/George Arceneaux/pacman/proto-game.cpp:125: undefined reference to `_glEnable@4'
/home/George Arceneaux/pacman/proto-game.cpp:126: undefined reference to `_glEnable@4'
/home/George Arceneaux/pacman/proto-game.cpp:127: undefined reference to `_glEnable@4'
/home/George Arceneaux/pacman/proto-game.cpp:128: undefined reference to `_glBlendFunc@8'
/home/George Arceneaux/pacman/proto-game.cpp:129: undefined reference to `_glHint@8'
collect2: ld returned 1 exit status
make: *** [proto-game] Error 1

Compilation exited abnormally with code 2 at Mon Jun  2 12:48:35





This is the code I am using.  This is just here in the event that something is wrong with it.  The main problem I think is in my makefile.

#include<iostream>
#include<iomanip>
#include<sstream>
using namespace std;
#include<vector>
#include<GL/glut.h>
#include<math.h>

int WIDTH = 500;  // width of the user window
int HEIGHT = 400;  // height of the user window
double facing_direction_x=200, facing_direction_y = 200;
double shape_position_x = 200, shape_position_y = 200; // position of the shape
double shape_width = 40, shape_height = 40; // size of the shape
double move_x = 50, move_y = 40; // how far to move for each keypress

// the display function actually does the work of drawing in the window.
//   this function will be called every time the appearance of the window
//   needs to be remade.
void display()
{
  // clear the buffer
  glClear(GL_COLOR_BUFFER_BIT);

  // let's draw a blue triangle
  glColor3f(1., 1., 0.);  // make it blue
  glBegin(GL_POLYGON);
glVertex2f(shape_position_x + 20, shape_position_y+30);
 glVertex2f(shape_position_x + shape_width, shape_position_y + shape_height);
 glVertex2f(shape_position_x + shape_width - 10, shape_position_y + shape_height + 10);
 glVertex2f(shape_position_x + shape_width - 30, shape_position_y + shape_height + 10);
   glVertex2f(shape_position_x, shape_position_y +shape_height);
  glVertex2f(shape_position_x, shape_position_y + 20);
 glVertex2f(shape_position_x + shape_width - 30, shape_position_y + shape_height + -30);
   glVertex2f(shape_position_x + shape_width - 10, shape_position_y + shape_height + -30);
   glVertex2f(shape_position_x + shape_width, shape_position_y +20);
   

  
  glEnd();

  // draw a red boundary
  /*glColor3f(1., 0., 1.);
  glBegin(GL_LINE_STRIP);
    glVertex2f(shape_position_x, shape_position_y);
    glVertex2f(shape_position_x + shape_width, shape_position_y);
    glEnd();*/

  // draw a yellow point
  /*glColor3f(1., 1., 0.);
  glBegin(GL_POINTS);
    glVertex2f(shape_position_x, shape_position_y);
    glEnd();*/

  // tell the graphics card that we're done-- go ahead and draw!
  glFlush();
}

// process keyboard events
void keyboard( unsigned char c, int x, int y )
{
  int win = glutGetWindow();
  switch(c) {
    case 'q':
    case 'Q':
    case 27:
      // get rid of the window (as part of shutting down)
      glutDestroyWindow(win);
      exit(0);
      break;
    case '\b':
      break;
    default:
      break;
  }
}

// process "special" keyboard events (those having to do with arrow keys)
void special_keyboard(int key,int x, int y)
{
  switch (key) {
    case GLUT_KEY_LEFT:
      shape_position_x -= move_x;
      break;
    case GLUT_KEY_RIGHT:
      shape_position_x += move_x;
      break;
    case GLUT_KEY_UP:
      shape_position_y += move_y;
        break;
    case GLUT_KEY_DOWN:
      shape_position_y -= move_y;
      break;
  }
  display();
}

// the reshape function handles the case where the user changes the size
//   of the window.  We need to fix the coordinate
//   system, so that the drawing area is still the unit square.
void reshape(int w, int h)
{
   glViewport(0, 0, (GLsizei) w, (GLsizei) h);
   WIDTH = w;  HEIGHT = h;
   glMatrixMode(GL_PROJECTION);
   glLoadIdentity();
   glOrtho(0., WIDTH-1, 0., HEIGHT-1, -1.0, 1.0);
}

// the init function sets up the graphics card to draw properly
void init(void)
{
  // clear the window to black
  glClearColor(0.0, 0.0, 0.0, 1.0);
  glClear(GL_COLOR_BUFFER_BIT);

  // set up the coordinate system:  number of pixels along x and y
  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();
  glOrtho(0., WIDTH-1, 0., HEIGHT-1, -1.0, 1.0);

  // set up how points and lines will be drawn.  The following
  //  commands make points and lines look nice and smooth.
  glPointSize(3);
  glLineWidth(1.5);
  glEnable(GL_POINT_SMOOTH);
  glEnable(GL_LINE_SMOOTH);
  glEnable(GL_BLEND);
  glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);
  glHint(GL_LINE_SMOOTH_HINT, GL_DONT_CARE);

  // welcome message
  cout << "Welcome to proto-game.  Use the arrow keys to move the shape around." << endl;
}

// init_gl_window is the function that starts the ball rolling, in
//  terms of getting everything set up and passing control over to the
//  glut library for event handling.  It needs to tell the glut library
//  about all the essential functions:  what function to call if the
//  window changes shape, what to do to redraw, handle the keyboard,
//  etc.
void init_gl_window()
{
  int argc = 1;
  char *argv[] = {"proto-game"};
  argc = sizeof(argv) / sizeof(argv[0]);
  glutInit(&argc, argv);
  glutInitDisplayMode( GLUT_RGB );
  glutInitWindowSize(WIDTH,HEIGHT);
  glutInitWindowPosition(100,100);
  glutCreateWindow("proto-game");
  init();

  glutDisplayFunc(display);
  glutReshapeFunc(reshape);
  glutKeyboardFunc(keyboard);
  glutSpecialFunc(special_keyboard);
  glutMainLoop();
}

int main()
{
  init_gl_window();
}



This is the Makefile
OPTS = -Wall -g
INCL = -I/usr/include -I/usr/include/GL
LIBS = -L/usr/X11R6/lib -lX11 -lXi -lXmu -lGLU -lGL -lglut -lm

proto-game: proto-game.cpp
	g++ $(OPTS) $(INCL) -o proto-game proto-game.cpp $(LIBS)




I am sure this is one of those easy beginner problems but if someone could help me, I would be ecstatic.

Thanks so much

---

### Post by LaRoza on 2008-06-02
Are you linking to the OpenGL libs?

---

### Post by boboclock367 on 2008-06-02
I suppose then my question becomes, how do I link the library?

---

### Post by geirha on 2008-06-02
This seems to be the same symptoms as you have [http://cygwin.com/ml/cygwin-xfree/2005-04/msg00114.html](http://cygwin.com/ml/cygwin-xfree/2005-04/msg00114.html) , so try the suggestion in the reply [http://cygwin.com/ml/cygwin-xfree/2005-04/msg00116.html](http://cygwin.com/ml/cygwin-xfree/2005-04/msg00116.html)

---


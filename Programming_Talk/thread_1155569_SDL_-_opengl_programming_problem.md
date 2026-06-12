---
title: "SDL - opengl programming problem"
date: 2009-05-10
forum: Programming Talk
---

### Post by dosh on 2009-05-10
I'm just learning SDL/Opengl and working through the "Redbook" and rewriting them using SDL rather then GLUT. In the example (changed slightly) I'm doing I have an interesting problem with the Translatef command if it is included I get a blank screen. If it is not I get some output, not all correctly of course as I need it to get it to display correctly. Please see below. Any help much appreciated as to why. GLUT works perfectly.

```
#include <GL/gl.h>
#include <GL/glu.h>
#include "SDL.h"
#include <stdlib.h>

#define TRUE 1
#define FALSE 0
int isActive;
GLuint listName;
void
init()
{
   listName = glGenLists (1);
   glNewList (listName, GL_COMPILE);
      glColor3f (1.0, 0.0, 0.0); /* current color red */
      glBegin (GL_TRIANGLES);
        glVertex2f (0.0, 0.0);
        glVertex2f (0.1, 0.0);
        glVertex2f (0.0, 0.1);
      glEnd ();
      
      /* move position */
   glEndList ();
   glShadeModel (GL_FLAT);
}

static void drawLine (void)
{
   glBegin (GL_LINES);
   glVertex2f (0.0, 0.5);
   glVertex2f (15.0, 0.5);
   glEnd ();
}

void display(void)
{
  GLuint i;

   glClear (GL_COLOR_BUFFER_BIT);
   glColor3f (0.0, 1.0, 0.0); /* current color green  */
  for (i = 0; i < 10; i++) {   /* draw 10 triangles  */
         glCallList (listName);
	glTranslatef (0.15,0.0, 0.0);}
   drawLine (); 
 
  SDL_GL_SwapBuffers();
}

/* new window size or exposure */
void reshape(int w, int h)
{
   glViewport(0, 0, w, h);
   glMatrixMode(GL_PROJECTION);
   glLoadIdentity();

   if (w <= h)
      gluOrtho2D (0.0, 2.0, -0.5 * (GLfloat) h/(GLfloat) w, 1.5 * (GLfloat) h/(GLfloat) w);
   else
      gluOrtho2D (0.0, 2.0*(GLfloat) w/(GLfloat) h, -0.5, 1.5);
 
   glMatrixMode(GL_MODELVIEW);
   glLoadIdentity();
  
}

int eventLoop(SDL_Surface *screen)
{
  int done=0;
  Uint8 *keys;
  SDL_Event event;
  

while ( SDL_PollEvent(&event) ) {
      switch(event.type) {
	case SDL_VIDEORESIZE:
          screen = SDL_SetVideoMode(event.resize.w, event.resize.h, 0, SDL_OPENGL|SDL_RESIZABLE);
          if ( screen ) {
            reshape(screen->w, screen->h);
          } else {
            /* Uh oh, we couldn't set the new video mode?? */;
          }
          break;

        case SDL_QUIT:
          done = 1;
          break;
      }
    }
    
    keys = SDL_GetKeyState(NULL);

    if ( keys[SDLK_ESCAPE] ) {
      done = 1;
    }
   
    return done;
}

int main(int argc, char *argv[])
{
  SDL_Surface *screen;
 

  SDL_Init(SDL_INIT_VIDEO);
  SDL_GL_SetAttribute( SDL_GL_RED_SIZE, 8 );
    SDL_GL_SetAttribute( SDL_GL_GREEN_SIZE, 8 );
    SDL_GL_SetAttribute( SDL_GL_BLUE_SIZE, 8 );
   SDL_GL_SetAttribute( SDL_GL_DOUBLEBUFFER, 1 );

  screen = SDL_SetVideoMode(650, 500, 0, SDL_OPENGL|SDL_RESIZABLE);
  if ( ! screen ) {
    fprintf(stderr, "Couldn't set 650x500 GL video mode: %s\n", SDL_GetError());
    SDL_Quit();
    exit(2);
  }
  SDL_WM_SetCaption("Redbook EX7-2", "Redbook");

  init();
  reshape(screen->w, screen->h);
  while ( ! eventLoop(screen) )
         display();
  SDL_Quit();
  return 0;             /* ANSI C requires main to return int. */
}
```

---

### Post by Sockerdrickan on 2009-05-11
Can you describe the output you are looking for, and I'll fix it.

---

### Post by dosh on 2009-05-11
Its not so much the output but the method as I am trying to learn and am curious at why the difference, between GLUT and my example. The output by the way is 10 triangles and a line. Now I could get that output but I am trying to work out why the glTranslatef is causing a problem. 

I just noticed this was my amended attempt. The glTranslatef was in the init function in the space as below

      ```

void init()
{
   listName = glGenLists (1);
   glNewList (listName, GL_COMPILE);
      glColor3f (1.0, 0.0, 0.0); /* current color red */
      glBegin (GL_TRIANGLES);
        glVertex2f (0.0, 0.0);
        glVertex2f (0.1, 0.0);
        glVertex2f (0.0, 0.1);
      glEnd ();
      glTranslatef (0.15,0.0, 0.0);      /* <<<Should be here */
      /* move position */
   glEndList ();
   glShadeModel (GL_FLAT);
}

static void drawLine (void)
{
   glBegin (GL_LINES);
   glVertex2f (0.0, 0.5);
   glVertex2f (15.0, 0.5);
   glEnd ();
}

void display(void)
{
  GLuint i;

   glClear (GL_COLOR_BUFFER_BIT);
   glColor3f (0.0, 1.0, 0.0); /* current color green  */
  for (i = 0; i < 10; i++)    /* draw 10 triangles  */
         glCallList (listName);  
/* NOT HERE */
  drawLine (); 
 
  SDL_GL_SwapBuffers();
}

```


This gives the the blank screen. Sorry about the first post. I still want to use a gl List and would like to put the glTranslatef in it that seems to cause the problem in SDL but not GLUT. Why is this so?

---

### Post by Sockerdrickan on 2009-05-11
```
void display(void)
{
  GLuint i;
    glLoadIdentity(); /*<---------- Have to reset modelview matrix or your triangles will appear moving*/
   glClear (GL_COLOR_BUFFER_BIT);
   glColor3f (0.0, 1.0, 0.0); /* current color green  */
  for (i = 0; i < 10; i++) {   /* draw 10 triangles  */
         glCallList (listName);
    glTranslatef (0.15,0.0, 0.0);}
   drawLine (); 
 
  SDL_GL_SwapBuffers();
}
```

---

### Post by dosh on 2009-05-11
Thanks Tux0r. Something simple like that. It was probably moving to quick and I thought the page was blank. Thanks again

---


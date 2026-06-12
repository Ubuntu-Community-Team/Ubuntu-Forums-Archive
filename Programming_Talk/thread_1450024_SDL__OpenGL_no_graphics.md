---
title: "SDL / OpenGL no graphics"
date: 2010-04-08
forum: Programming Talk
---

### Post by j.bell730 on 2010-04-08
I'm trying to learn SDL and OpenGL. I'm just starting out creating simple 2d polygons (a triangle, actually). But nothing is showing up in the window. All I get is just a completely black window. I'm writing in C.

Here is my code:
[PHP]#include "SDL/SDL.h"
#include <GL/gl.h>
#include <GL/glu.h>

int main (int argc, char* args[])
{
    SDL_Surface* screen = NULL;
    
    int screenWidth = 1024;
    int screenHeight = 768;
    int screenBPP = 32;
    
    SDL_Init (SDL_INIT_EVERYTHING);
    
    SDL_GL_SetAttribute (SDL_GL_RED_SIZE, 8);
    SDL_GL_SetAttribute (SDL_GL_GREEN_SIZE, 8);
    SDL_GL_SetAttribute (SDL_GL_BLUE_SIZE, 8);
    
    screen = SDL_SetVideoMode (screenWidth, screenHeight, screenBPP, SDL_SWSURFACE);
    
    glClear (GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glLoadIdentity ();
    
    glTranslatef (0.0f, 0.0f, 0.0f);
    
    glBegin (GL_TRIANGLES);
    glColor3f (1.0f, 0.0f, 0.0f);
    glVertex3f (0.0f, 1.0f, 0.0f);
    glColor3f (0.0f, 1.0f, 0.0f);
    glVertex3f (1.0f, -1.0f, 0.0f);
    glColor3f (0.0f, 0.0f, 1.0f);
    glVertex3f (-1.0f, -1.0f, 0.0f);
    glEnd ();
    
    SDL_Flip (screen);
    
    SDL_Delay (3000);
    
    SDL_Quit ();
    
    return 0;
}[/PHP]

I'm compiling with:
```
gcc sdl.c -lSDL -lGL
```

What is it that I'm doing wrong?

---

### Post by Sockerdrickan on 2010-04-08
You need to set up your projection matrix, use gluLookAt or something.

---


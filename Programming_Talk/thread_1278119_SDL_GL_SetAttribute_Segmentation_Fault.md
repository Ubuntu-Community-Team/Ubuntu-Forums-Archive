---
title: "SDL_GL_SetAttribute Segmentation Fault"
date: 2009-09-29
forum: Programming Talk
---

### Post by jommoner on 2009-09-29
Hi!

I'm using codeblocks IDE, and trying SDL/OpenGL programming. I can compile the code below without errors, but then it crashes with a segmentation fault:

#ifdef __cplusplus
    #include <cstdlib>
#else
    #include <stdlib.h>
#endif
#ifdef __APPLE__
#include <SDL/SDL.h>
#else
#include <SDL.h>
#endif

#include <GL/gl.h>

int main ( int argc, char** argv )
{  SDL_Event event;
   float theta = 0.0f;
   SDL_GL_SetAttribute( SDL_GL_RED_SIZE, 8 );
   SDL_GL_SetAttribute( SDL_GL_BLUE_SIZE, 8 );
   SDL_GL_SetAttribute( SDL_GL_GREEN_SIZE,8 );
   SDL_GL_SetAttribute(SDL_GL_BUFFER_SIZE, 32 );
   SDL_Init(SDL_INIT_VIDEO);
   SDL_SetVideoMode(300, 300, 0, SDL_OPENGL | SDL_HWSURFACE | SDL_NOFRAME);

   glViewport(0, 0, 300, 300);
   glClearColor(0.2f, 0.2f, 0.2f, 0.0f);
   glClearDepth(1.0);
   glDepthFunc(GL_LESS);
   glEnable(GL_DEPTH_TEST);
   glShadeModel(GL_SMOOTH);
   glMatrixMode(GL_PROJECTION);
   glMatrixMode(GL_MODELVIEW);

    int done;
   for(done = 0; !done;)
   {
     glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

     glLoadIdentity();
     glTranslatef(0.0f,0.0f,0.0f);
     glRotatef(theta, 0.0f, 0.0f, 1.0f);
     glBegin(GL_TRIANGLES);
     glColor3f(1.0f, 0.0f, 0.0f);
     glVertex2f(0.0f, 1.0f);
     glColor3f(0.0f, 1.0f, 0.0f);
     glVertex2f(0.87f, -0.5f);
     glColor3f(0.0f, 0.0f, 1.0f);
     glVertex2f(-0.87f, -0.5f);
     glEnd();

     theta += .05f;
     SDL_GL_SwapBuffers();
     SDL_PollEvent(&event);
     if(event.key.keysym.sym == SDLK_ESCAPE)
       done = 1;
   }
}


If I remove the stuff at the start (this:

   SDL_GL_SetAttribute( SDL_GL_RED_SIZE, 8 );
   SDL_GL_SetAttribute( SDL_GL_BLUE_SIZE, 8 );
   SDL_GL_SetAttribute( SDL_GL_GREEN_SIZE,8 );
   SDL_GL_SetAttribute(SDL_GL_BUFFER_SIZE, 32 );

)

Then it runs fine!

If I compile the following code:

int main ( int argc, char** argv )
{  SDL_Event event;
   float theta = 0.0f;
   SDL_GL_SetAttribute( SDL_GL_RED_SIZE, 8 );
}

Then it compiles fine, but crashes with a segmentation fault.

If I remove the SDL_GL line above, and replace it with:
SDL_GL_SetAttribute()

Then it compiles fine, but crashes with a segmentation fault.

Any idea what might be happening here? Is there any reason why the SDL_GL_SetAttribute command is off-limits in Linux? 

My computer has an ATI X2300, with the closed source drivers installed. Wine works fine with OpenGL acceleration, desktop effects etc work fine - the driver itself is fine.

Thanks for your help!

---

### Post by Zugzwang on 2009-09-29
You *will* have to init SDL first and then *might* have to set up the graphics mode before you can apply attributes.

---

### Post by jommoner on 2009-09-29
Hi!

Thanks for the advice - that fixed it :)

The error was from : [http://www.devshed.com/c/a/Multimedia/Using-OpenGL-with-SDL-for-Game-Programming/3/](http://www.devshed.com/c/a/Multimedia/Using-OpenGL-with-SDL-for-Game-Programming/3/) which is why it was exasperating for me (assumed I had set the compiler up wrong or something!)

Thanks again!

---

### Post by hessiess on 2009-09-29
You should also pass SDL_RESIZABLE to SDL_SetVideoMode and catch window resize events to make your application resolution independent.

---


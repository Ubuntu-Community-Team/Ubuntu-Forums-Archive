---
title: "Drawing simple 2d shapes with SDL"
date: 2007-02-09
forum: Programming Talk
---

### Post by Randomskk on 2007-02-09
Does anyone know of any simple methods for drawing basic 2d shapes (ie, squares and circles) to the screen in SDL without having to load a texture of the shape and scale it and such?
I'm trying to just draw a simple circle, but can't figure out how to actually made SDL draw anything. Alternatively, would it be possible to do this using OpenGL? I've not tried drawing 2d shapes in OpenGL before, but I know it can manage simple 3d shapes easily.

Thanks for any help!

---

### Post by Wybiral on 2007-02-09
With OpenGL it would actually be very simple... Just set the screen to an ortho display like this...
```

	glViewport( 0, 0, width, height );
	glMatrixMode( GL_PROJECTION );
	glOrtho( 0, width, height, 0, -1, 1 );
	glMatrixMode( GL_MODELVIEW );

```
Instead of setting it up for 3d perspective with glu and you will have a typical 2d setup to render on.

You can also use things like glVertex2i instead of glVertex3f

Also, it's much faster if you disable depth testing and don't bother clearing the depth buffer when you render.

---

### Post by Wybiral on 2007-02-09
Also, this probably isn't the most efficient method, but this will work as a circle function:

```

// g++ me.cpp -lSDL -lGL 

#include <math.h>
#include <GL/gl.h>
#include <SDL/SDL.h>

#define RAD2DEG 0.0174532925

void init(int width, int height)
{
	// Initialize SDL
	const SDL_VideoInfo* info = NULL;
	SDL_Init(SDL_INIT_VIDEO);
	info = SDL_GetVideoInfo();	
	int vidFlags = SDL_OPENGL | SDL_GL_DOUBLEBUFFER;
	if (info->hw_available) {vidFlags |= SDL_HWSURFACE;}
	else {vidFlags |= SDL_SWSURFACE;}
	SDL_SetVideoMode(width, height, info->vfmt->BitsPerPixel, vidFlags);

	// Initialize OpenGL for 2d
	glViewport( 0, 0, width, height );
	glMatrixMode( GL_PROJECTION );
	glOrtho( 0, width, height, 0, -1, 1 );
	glMatrixMode( GL_MODELVIEW );
   glDisable(GL_DEPTH_TEST);
}

void glCircle(GLint x, GLint y, GLint r)
{
   float step = 360.0 / (2.0*M_PI*r);
   glPushMatrix();
   glTranslatef(x, y, 0);
   glBegin(GL_TRIANGLE_FAN);
   glVertex2i(0, 0);
   for(float i=0; i<360; i+=step)
   {
      glVertex2i((GLint)(cos(RAD2DEG*i)*r), (GLint)(sin(RAD2DEG*i)*r));
   }
   glEnd();
   glPopMatrix();
}

int main()
{
   init(640, 480);
   glClear(GL_COLOR_BUFFER_BIT);
	glLoadIdentity();
   glCircle(200, 200, 100);
	SDL_GL_SwapBuffers();
	SDL_Delay(2000);
}

```

---

### Post by Randomskk on 2007-02-09
Thanks!
Do you know of any good SDL OGL tutorials? I've just realised I've only done 2d in SDL, everything I've done in OGL has been with [GLFW](http://glfw.sourceforge.net/).

---

### Post by Skardal on 2007-02-11
[LIST]
[*][NeHe]("http://nehe.gamedev.net") <-- Awsome OpenGL site!
[*][LazyFoo]("http://lazyfooproductions.com") <-- Many good tutorials on SDL, and one of them are how to use OpenGL from within SDL! :)
[*][Cone3d]("http://cone3d.gamedev.net") <-- Both SDL and OpenGL. Not together though...
[/LIST]

Hope some of them can help you :)

---


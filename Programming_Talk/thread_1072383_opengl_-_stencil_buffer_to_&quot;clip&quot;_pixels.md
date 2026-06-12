---
title: "opengl - stencil buffer to &quot;clip&quot; pixels"
date: 2009-02-17
forum: Programming Talk
---

### Post by ch42 on 2009-02-17
Hi, I am trying to use the stencil buffer to clip (i.e. don't allow drawing) on a specific part of the screen (2d).
I tried to implement the instructions at [http://www.videotutorialsrock.com/opengl_tutorial/reflections/text.php](http://www.videotutorialsrock.com/opengl_tutorial/reflections/text.php), but somehow it doesn't work.
I'd expect the green rectangle to not be drawn in the space that the white rectangle occupies.

```

#include <SDL.h>
#include <SDL_opengl.h>


int main() {
	if (SDL_Init(SDL_INIT_VIDEO | SDL_INIT_TIMER) == -1) {
        printf("Can't init SDL:  %s\n", SDL_GetError());
        exit(1);
    }
	SDL_Surface *screen;
	screen = SDL_SetVideoMode(500, 500, 32, SDL_HWSURFACE | SDL_OPENGL);
    if (screen == NULL) {
        printf("Can't set video mode: %s\n", SDL_GetError());
        exit(1);
    }
    
	SDL_GL_SetAttribute(SDL_GL_DOUBLEBUFFER, 1);
	
	// basic viewport
	gluOrtho2D(0, 500, 0, 500);
	
	// Stenceling
	
	glClearStencil(0);
	glClear(GL_STENCIL_BUFFER_BIT);
	glEnable(GL_STENCIL_TEST);
	
	glStencilFunc(GL_ALWAYS, 1, 1);
	glStencilOp(GL_KEEP, GL_KEEP, GL_REPLACE);
	
	
	glRecti(0, 0, 100, 100);
	
	
	glStencilFunc(GL_EQUAL, 1, 1);
	glStencilOp(GL_KEEP, GL_KEEP, GL_KEEP);
	
	
	
	glColor3f(0, 1, 0);
	
	glRecti(50, 50, 300, 300);
	
	
    SDL_GL_SwapBuffers();
	
	SDL_Delay(5000);

}

```

Also see the attached screenshot.

Thanks!

---

### Post by ch42 on 2009-03-02
bump

---

### Post by stroyan on 2009-03-02
It looks like you got a window without any stencil buffer bits.
You need to specify the minimum stencil bits or SDL may use a visual with none.
```

    SDL_GL_SetAttribute(SDL_GL_STENCIL_SIZE, 1);

```
You need to make your calls to **SDL_GL_SetAttribute** *before*
calling **SDL_SetVideoMode**.
You can check the values that you actually got by calling **SDL_GetAttribute**.

---

### Post by ch42 on 2009-03-03
Thanks a lot!

---


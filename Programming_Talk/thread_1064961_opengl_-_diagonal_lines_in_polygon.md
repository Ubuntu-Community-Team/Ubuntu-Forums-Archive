---
title: "opengl - diagonal lines in polygon"
date: 2009-02-09
forum: Programming Talk
---

### Post by ch42 on 2009-02-09
Hi, I have the following simple C++ sdl/opengl code:
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
	
	// antialiasing
	glBlendFunc (GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);
	glEnable (GL_BLEND);
	glEnable(GL_POINT_SMOOTH);
	glEnable(GL_LINE_SMOOTH);
	glEnable(GL_POLYGON_SMOOTH);
	
	
	glColor3f(0, 1, 0);
	
	glRecti(50, 50, 300, 300);
	
	
        SDL_GL_SwapBuffers();
	
	SDL_Delay(5000);

}

```

Now, I'd expect a filled green rectangle to appear. But: the rectangle has a thin black diagonal line from the lower left to the upper right corner. (See attached Screenshot).
Why does this diagonal line appear? How can I make it go away?

Thanks, ch42

---

### Post by stroyan on 2009-02-09
I blame your hardware.  It is normal that rectangles are decomposed into triangles before rendering.  That can cause shading artifacts during color interpolation.  But it should not cause an obvious gap like your capture shows.  The two triangles should be meeting seamlessly.

---

### Post by ch42 on 2009-02-10
> **stroyan said:**
> I blame your hardware.  It is normal that rectangles are decomposed into triangles before rendering.  That can cause shading artifacts during color interpolation.  But it should not cause an obvious gap like your capture shows.  The two triangles should be meeting seamlessly.

I am using ubuntu intrepid 64 bit with the nvidia restricted graphics driver. (version 177, the recommended driver in jockey).

What can I do in order for the diganoal lines to disappear?

---

### Post by haemulon on 2009-02-10
Have you tried drawing the rectangle using the geometric primitives (GL_TRIANGLES) instead of glRect?

The video card could have a poorly implemented glRect function.

Also try it with the 3D version glOrtho and see what happens.

---

### Post by Gordon Bennett on 2009-02-10
The problem is with:

glEnable(GL_POLYGON_SMOOTH);

Which causes these anomalies due to on-edge blending issues and the Z-buffer (if it is enabled).

The solution is to use a saturated blend function instead:

glBlendFunc(GL_SRC_ALPHA_SATURATE, GL_ONE);

To have it work properly, the Z-buffer has to be disabled.

Otherwise, if you want all the trimmings, you can just enable FSAA :P

---

### Post by ch42 on 2009-02-10
> **Gordon Bennett said:**
> The problem is with:

glEnable(GL_POLYGON_SMOOTH);

Which causes these anomalies due to on-edge blending issues and the Z-buffer (if it is enabled).

The solution is to use a saturated blend function instead:

glBlendFunc(GL_SRC_ALPHA_SATURATE, GL_ONE);

To have it work properly, the Z-buffer has to be disabled.


I tried changing the glBlendFunc to your suggestion and putting in glDisable(GL_DEPTH_TEST);
but then it won't display anything (i.e. screen all black, no green rectangle at all).

---

### Post by geirha on 2009-02-10
I tried your code myself, and I also get a line like you do, except it goes from bottom right to top left. I'm using the open source radeon driver, so I don't think it's a driver issue.

---

### Post by Zugzwang on 2009-02-10
From a logical point of view, if you want "correct" AA (aka smoothing), the graphic card/drawer would need to keep track of the Z-levels for parts of the pixels. This is normally overkill and requires defining the parts of each individual pixel, so this not done behind the scenes. My solution would be to enable AA for the whole screen, i.e. to render it at four times the resolution and then scale it down.

---

### Post by Gordon Bennett on 2009-02-10
> **ch42 said:**
> I tried changing the glBlendFunc to your suggestion and putting in glDisable(GL_DEPTH_TEST);
but then it won't display anything (i.e. screen all black, no green rectangle at all).

How odd - this is standard procedure and it should work - so I compiled your code with the fix and indeed I have the same result on my nVidia 7800GTX.

This should work (I used to write OpenGL drivers :P ) - so I tried the same solution on my laptop with a cruddy ATI 340M chipset, which uses the cast-iron Mesa driver - it works as intended!

Folks - *we have a bug in the nVidia driver* :)

---

### Post by hessiess on 2009-02-10
+1 for drawing using two triangles

---

### Post by ch42 on 2009-02-10
Well, I didn't really want to find a bug in nvidia drivers... all I wanted to do is drawing a Polygon with opengl. :(

Can somebody more experienced with opengl report the bug to nvidia? I'm new to opengl and just found this weird problem, I think it would be more usefull for nvidia if somebody with more knowledge about opengl would report the bug.

So I'll just have to cross my fingers nvidida gets this bug fixed soon. :(

Thanks for all your help!

---

### Post by Gordon Bennett on 2009-02-10
> **ch42 said:**
> Well, I didn't really want to find a bug in nvidia drivers... all I wanted to do is drawing a Polygon with opengl. :(

Can somebody more experienced with opengl report the bug to nvidia? I'm new to opengl and just found this weird problem, I think it would be more usefull for nvidia if somebody with more knowledge about opengl would report the bug.

So I'll just have to cross my fingers nvidida gets this bug fixed soon. :(

Thanks for all your help!

Depends what you want to do with your code - if you want to draw antialiased OpenGL that is guaranteed to work then you can use FSAA - it's pretty easy to set up, supports depth-buffering and with the fillrate plus RAM of cards released in the past three years, you don't have to worry about bringing the GPU to its knees.

If you do decide to use it, make it optional for the user to enable.

The reason why I suggest you use FSAA instead of waiting for a driver fix is that bugs like these usually have an arbitrary timescale to fix and is usually inversely proportional to the marketing benefit for the company :P

Case in point, a huge firewire audio bug took Apple more than a year to fix, despite the solution being simple - it was just not in their top marketing checkboxes to bother themselves about, despite large amounts of device manufacturers having their reputations hammered to the ground because of it.

So, I suggest you make FSAA optional and save yourself the wait ;)

---

### Post by ch42 on 2009-02-10
This page ([http://homepage.mac.com/arekkusu/bugs/invariance/FSAA.html](http://homepage.mac.com/arekkusu/bugs/invariance/FSAA.html)) doesn't put a too positive light on FSAA.
But anyway, getting these lines away is not really essential for me, I think I'll wait for nvidia to fix the bug. Does nvidia know that the bug exists?

---

### Post by Gordon Bennett on 2009-02-10
> **ch42 said:**
> This page ([http://homepage.mac.com/arekkusu/bugs/invariance/FSAA.html](http://homepage.mac.com/arekkusu/bugs/invariance/FSAA.html)) doesn't put a too positive light on FSAA.
But anyway, getting these lines away is not really essential for me, I think I'll wait for nvidia to fix the bug. Does nvidia know that the bug exists?

That's a pretty old page though - FSAA has moved on quite a bit since then!

For most OpenGL apps FSAA (or antialiasing as a whole) is considered optional, since the higher screen resolution/DPI, the less need there is for it.

I don't know if nVidia know if the bug exists - whether any of us humble coders can be bothered to take time out from our days to do what is supposed to be the job of a multi-million-dollar-company is another matter :)

---


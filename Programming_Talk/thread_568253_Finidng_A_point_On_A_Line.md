---
title: "Finidng A point On A Line"
date: 2007-10-05
forum: Programming Talk
---

### Post by Lster on 2007-10-05
Hi everyone

This is a maths problem I'm having related to programming. I have posted a diagram as an attachment that may help.

...Edited...

Thanks,
Lster

---

### Post by Lster on 2007-10-05
Woops! I forgot the attachment... Here is is!

---

### Post by Lster on 2007-10-05
3rd hour lucky! I've just managed my problem, myself!

Sorry guys,
Lster

---

### Post by dwhitney67 on 2007-10-06
Great!  It's good to know that your computer is working well for you.

---

### Post by Lster on 2007-10-06
I forgot to say: if anyone is interested, I can post my method.

---

### Post by Note360 on 2007-10-06
post it. its always fun to see this stuff.

---

### Post by Lster on 2007-10-06
...Edited...

Lster

---

### Post by SpiritIsReality on 2007-10-06
howdy
great stuff
I was going to say, map and compass?
what's the fancy word for that again?
buds

---

### Post by Lster on 2007-10-06
And here's the diagram!

---

### Post by Lster on 2007-10-06
> I was going to say, map and compass?
what's the fancy word for that again?

Do you mean coordinates? Cause this is basically just coordinate geometry.

---

### Post by slavik on 2007-10-06
went through your math and I agree that your method should be correct. :)

---

### Post by hod139 on 2007-10-06
Your solution is very good, however your program will break if you have a verticle line (m = infinity).  Using your solution, you have to special case if m > big

What class is this for?  If you know trig you can use sin and cos to solve this.

---

### Post by Lster on 2007-10-06
> went through your math and I agree that your method should be correct. 

Great! :)

> Your solution is very good, however your program will break if you have a verticle line (m = infinity). Using your solution, you have to special case if m > big

Yeah. That's already taken care of...

> What class is this for? If you know trig you can use sin and cos to solve this.

It's not for college. I just needed it in a game I'm programming. You see I want a rectangle that always faces the camera...

---

### Post by SpiritIsReality on 2007-10-06
> **Lster said:**
> Do you mean coordinates? Cause this is basically just coordinate geometry.
ya right. Navigation. GPS Way to go. thanks
(not important, there's some fancy boy scout word for reading and using a compass and walking around)
dictionary doesn't go in reverse as far as I know, unless you use a command line search on the directory or something. and I'm not havin much success with google, except to hit places that are willing to teach me navigational skills, and gps) free and online,!!!! Very Cool ...
buds
got it,
orienteering. thanks for reminding me.

---

### Post by Wybiral on 2007-10-06
> **Lster said:**
> It's not for college. I just needed it in a game I'm programming. You see I want a rectangle that always faces the camera. That way individual particles (in my particle engine) are shown correctly.

The method I used was:

I know where the camera is and where the rectangle has to be positioned. So I find the line between those two points and then the perpendicular bisector of it (except so that it passes through the point where the rectangle has to be). Then I solve the simultaneous equation that I posted...

I may be misinterpreting this, but it sound like you want to billboard some polygons? If that's the case (and assuming you're using OpenGL), then there's an easier method... Mask out the rotation from the model-view matrix.

Here's a quick example (the billboard function is all you need to see):
```

/* gcc -std=c99 billboard.c `sdl-config --cflags --libs` -lGLU -lGL */

#include <GL/gl.h>
#include <GL/glu.h>
#include <SDL/SDL.h>

/* Initialize SDL and setup GL projection */
SDL_Surface *init_sdl(const int width, const int height)
{
    SDL_Init(SDL_INIT_VIDEO);
    const SDL_VideoInfo* info = SDL_GetVideoInfo();
    const int flags = SDL_OPENGL | SDL_GL_DOUBLEBUFFER;
    return SDL_SetVideoMode(width, height, info->vfmt->BitsPerPixel, flags);
}

/* Setup GL projection */
void init_gl(const int width, const int height)
{
    glViewport(0, 0, width, height);
    glMatrixMode(GL_PROJECTION);
    gluPerspective(60, (GLfloat)width / height,  1, 6000);

    glMatrixMode(GL_MODELVIEW);
    glEnable(GL_DEPTH_TEST);
}

/* Ensure that the window has not been closed */
unsigned char running()
{
    SDL_Event e;
    while(SDL_PollEvent(&e))
    {
        if(e.type == SDL_KEYDOWN && e.key.keysym.sym == SDLK_ESCAPE) return 0;
        else if(e.type == SDL_QUIT) return 0;
    }
    return 1;
}

/* Grab modelview matrix, mask out rotation, load new matrix */
void billboard()
{
    float m[16];
    glGetFloatv(GL_MODELVIEW_MATRIX, m);
    memset(m, 0, sizeof(float)*12);
    m[0]=m[5]=m[10]=1.0;
    glLoadMatrixf(m);
}

int main(int argc, char *argv[])
{
    SDL_Surface *surf = init_sdl(640, 480);
    init_gl(640, 480);

    /* Create random particles */
    GLint particle[5000][3];
    GLubyte rgb[5000][3];
    for(int i=0; i<5000; i++)
    {
        for(int n=0; n<3; n++)
        {
            rgb[i][n] = rand() % 256;
            particle[i][n] = (rand() % 100) - 50;
        }
    }

    float angle = 0.0;
    while(running())
    {
        glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
        glLoadIdentity();
        glTranslatef(0, 0, -200);
        glRotatef(angle, 1, 1, 0);
        for(int i=0; i<5000; i++)
        {
            glPushMatrix();
            glTranslatef(particle[i][0], particle[i][1], particle[i][2]);
            billboard();
            glBegin(GL_QUADS);
            glColor3ubv(rgb[i]);
            glVertex2i(-1, -1);
            glVertex2i( 1, -1);
            glVertex2i( 1,  1);
            glVertex2i(-1,  1);
            glEnd();
            glPopMatrix();
        }
        SDL_GL_SwapBuffers();
        angle += 0.1;
    }
    SDL_FreeSurface(surf);
    SDL_Quit();
    return 0;
}

```

---

### Post by Lster on 2007-10-07
Wow, that is easy. I am not very good with matrices (we have just started them at college in Further Maths).

Thanks Wybiral!

---

### Post by Wybiral on 2007-10-07
> **Lster said:**
> Wow, that is easy. I am not very good with matrices (we have just started them at college in Further Maths). Anyway, with a little probing it appears that calling billboard ( ) turns the following object towards the camera - is this right?

Thanks Wybiral!

Basically. Since the modelview matrix stores your transformations, all you need to do to remove the rotation is mask those components back to the identity matrix. Then your polygons will be rendered as if there were no rotational transformations. Since you don't alter the translation components, the objects remain in their coordinate location.

---

### Post by Lster on 2007-10-07
That's cool - thanks! I'll be using that now... :)

---


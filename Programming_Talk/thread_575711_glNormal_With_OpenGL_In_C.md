---
title: "glNormal With OpenGL In C"
date: 2007-10-14
forum: Programming Talk
---

### Post by Lster on 2007-10-14
Hi guys

I'm sorry to post on something so simple but I am having more trouble than expected with normals.

...Edited...

Thanks,
Lster

---

### Post by Wybiral on 2007-10-14
The normal for a surface is a normalized vector pointing away from the surface, perpendicular to the plane. So if your surface normal for the top of a cube is (0, 1, 0). The surface normal for the bottom of that cube is (0, -1, 0). These, of course, are if you're outside the cube (and they're reversed if you're inside).

Usually the normals are calculated like this (these are 3d vectors btw):
```

temp1 = vert[1] - vert[0];
temp2 = vert[2] - vert[1];
norm = cross_product(temp1, temp2);
normalize(norm);

```

Here's an example in C of calculating the normal. If you change the triangle some (by altering the vectors set in "main()" by "vec3_set()") you'll notice that the yellow line remains perpendicular to the triangle. That's exactly what you want for your normals. Naturally you need to normalize them (scale them to a length of one).

The function you'll probably want to look at is "triangle_recalc()" which is where the normal calculation goes on. "vec3" is my simple 3d vector structure, the functions are similar to intel assembly in that "op dst, src".

```

/* gcc -std=c99 normal.c `sdl-config --cflags --libs` -lGLU -lGL */

#include <math.h>
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

/* vec3 = 3 floats */
typedef float vec3[3];

/* Set x,y,z of vec3 */
void vec3_set(vec3 vec, const float x, const float y, const float z)
{
    vec[0] = x;
    vec[1] = y;
    vec[2] = z;
}

/* Copy vec3 */
void vec3_cpy(vec3 a, const vec3 b)
{
    a[0] = b[0];
    a[1] = b[1];
    a[2] = b[2];
}

/* Subtract vec3 */
void vec3_sub(vec3 a, const vec3 b)
{
    a[0] -= b[0];
    a[1] -= b[1];
    a[2] -= b[2];
}

/* Add vec3 */
void vec3_add(vec3 a, const vec3 b)
{
    a[0] += b[0];
    a[1] += b[1];
    a[2] += b[2];
}

/* Crossproduct vec3 */
void vec3_cross(vec3 dest, const vec3 a, const vec3 b)
{
    dest[0] = a[1] * b[2] - a[2] * b[1];

    dest[1] = a[2] * b[0] - a[0] * b[2];

    dest[2] = a[0] * b[1] - a[1] * b[0];
}

/* Scale vec3 */
void vec3_scale(vec3 a, const float s)
{
    a[0] *= s;
    a[1] *= s;
    a[2] *= s;
}

/* Normalize vec3 */
void vec3_normalize(vec3 vec)
{
    float len = sqrt(vec[0]*vec[0] + vec[1]*vec[1] + vec[2]*vec[2]);
    if(len != 0.0)
    {
        len = 1.0 / len;
        vec[0] *= len;
        vec[1] *= len;
        vec[2] *= len;
    }
}

/* Simple triangle structure */
typedef struct
{
    vec3 vert[3];
    vec3 norm;
} triangle;

/* Calculate lighting face-normals */
void triangle_recalc(triangle *tri)
{
    vec3 a, b, c;
    vec3_cpy(a, tri->vert[1]);
    vec3_sub(a, tri->vert[0]);
    vec3_cpy(b, tri->vert[2]);
    vec3_sub(b, tri->vert[1]);
    vec3_cross(c, a, b);
    vec3_normalize(c);
    vec3_cpy(tri->norm, c);
}

/* Render triangle (and normal vector) */
void triangle_render(triangle *tri)
{
    glBegin(GL_TRIANGLES);
    glColor3ub(0xff, 0x00, 0x00); glVertex3fv(tri->vert[0]);
    glColor3ub(0x00, 0xff, 0x00); glVertex3fv(tri->vert[1]);
    glColor3ub(0x00, 0x00, 0xff); glVertex3fv(tri->vert[2]);
    glEnd();

    vec3 center;
    vec3_cpy(center, tri->vert[0]);
    vec3_add(center, tri->vert[1]);
    vec3_add(center, tri->vert[2]);
    vec3_scale(center, 1.0 / 3.0);

    glColor3ub(0xff, 0xff, 0x00);
    glBegin(GL_LINES);
    glVertex3fv(center);
    vec3_add(center, tri->norm);
    glVertex3fv(center);
    glEnd();
}

int main(int argc, char *argv[])
{
    SDL_Surface *surf = init_sdl(640, 480);
    init_gl(640, 480);

    float angle = 0.0;

    triangle tri;
    vec3_set(tri.vert[0], 0.5, 0.0, 0.0);
    vec3_set(tri.vert[1], 0.0, 1.0, 0.0);
    vec3_set(tri.vert[2], 1.0, 1.0, 0.0);
    triangle_recalc(&tri);

    while(running())
    {
        glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
        glLoadIdentity();
        glTranslatef(0, 0, -3);
        glRotatef(angle, 1, 1, 0);
        glRotatef(angle, 0, 1, 0);
        triangle_render(&tri);
        SDL_GL_SwapBuffers();
        angle += 0.05;
    }

    SDL_FreeSurface(surf);
    SDL_Quit();
    return 0;
}

```

---

### Post by Wybiral on 2007-10-14
Oh, I just noticed you're using a pretty simply surface. You're right with the (0, 1, 0) normal. You have LIGHT1 on, but have you turned lighting on? 

```

glEnable(GL_LIGHTING);

```

---

### Post by Lster on 2007-10-14
> You have LIGHT1 on, but have you turned lighting on? 

No, lighting is definitely enabled.

Thank you for the generic code I aim to implement that once I get the grounds mapping working.

Thanks,
Lster

---

### Post by Wybiral on 2007-10-14
What does it look like (how does it look wrong)? You may need to post some code.

---

### Post by Lster on 2007-10-14
I just don't get any light on the grass. I have some grass (which stands up straight) that is lighted correctly using the normal for the ground.

---

### Post by Lster on 2007-10-15
*Bump*

Anyone?

---


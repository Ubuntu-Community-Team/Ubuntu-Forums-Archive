---
title: "Displaying a 2d texture in 2d space OpenGL"
date: 2010-07-16
forum: Programming Talk
---

### Post by Eragon0605 on 2010-07-16
I am able to load a texture as a GLuint using SOIL, but I don't know where to go from here to get it actually on the screen. I found all kinds of tutorials on how to apply attributes to the texture to make all kinds of fancy lighting effects and how to wrap it around cubes and stuff, but I don't give a rip about that at the moment. I just want to know how to display my loaded texture in a 2d environment I have already set up. I am using OpenGL and GLUT.

---

### Post by Sockerdrickan on 2010-07-16
Set up projection and render it by binding the texture and drawing vertices/texture coordinates like a rectangle!

---

### Post by Eragon0605 on 2010-07-16
Ok, so I did all that, and followed the example in the redbook. I get a nice black square. Hrm, my texture is bright red. Anyways, here is the relevant code I am working with:
```

    glEnable(GL_TEXTURE_2D);

    glBindTexture(GL_TEXTURE_2D, tex_2d);
   
    glBegin(GL_QUADS);
        glTexCoord2f(0.0, 0.0); glVertex2f(-8.0f, -8.0f);
        glTexCoord2f(1.0, 0.0); glVertex2f(8.0f, -8.0f);
        glTexCoord2f(1.0, 1.0); glVertex2f(8.0f, 8.0f);
        glTexCoord2f(0.0, 1.0); glVertex2f(-8.0f, 8.0f);
    glEnd();

    glutSwapBuffers();
    glDisable(GL_TEXTURE_2D);
```Oh, and here is my SOIL code, in case I am doing something wrong there:
```

GLuint tex_2d = SOIL_load_OGL_texture
    (
        "circle.png",
        SOIL_LOAD_RGBA,
        SOIL_CREATE_NEW_ID,
        SOIL_FLAG_TEXTURE_RECTANGLE | SOIL_FLAG_NTSC_SAFE_RGB
    );
```

---

### Post by Sockerdrickan on 2010-07-16
> **Eragon0605 said:**
> Ok, so I did all that, and followed the example in the redbook. I get a nice black square. Hrm, my texture is bright red. Anyways, here is the relevant code I am working with:
```

    glEnable(GL_TEXTURE_2D);

    glBindTexture(GL_TEXTURE_2D, tex_2d);
   
    glBegin(GL_QUADS);
        glTexCoord2f(0.0, 0.0); glVertex2f(-8.0f, -8.0f);
        glTexCoord2f(1.0, 0.0); glVertex2f(8.0f, -8.0f);
        glTexCoord2f(1.0, 1.0); glVertex2f(8.0f, 8.0f);
        glTexCoord2f(0.0, 1.0); glVertex2f(-8.0f, 8.0f);
    glEnd();

    glutSwapBuffers();
    glDisable(GL_TEXTURE_2D);
```Oh, and here is my SOIL code, in case I am doing something wrong there:
```

GLuint tex_2d = SOIL_load_OGL_texture
    (
        "circle.png",
        SOIL_LOAD_RGBA,
        SOIL_CREATE_NEW_ID,
        SOIL_FLAG_TEXTURE_RECTANGLE | SOIL_FLAG_NTSC_SAFE_RGB
    );
```
Okay that looks good for the drawing part, what about setting up projection? Did you do that? Post the full code if so

---

### Post by Eragon0605 on 2010-07-16
[LEFT]Oh, I have to do something special for textures? I have set up a normal projection, so I can draw images and stuff. Here is all my stuff:
```

    GLfloat aspectRatio;

    if(h == 0)
        h = 1;

    glViewport(0, 0, w, h);

    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();

    aspectRatio = (GLfloat)w / (GLfloat)h;
    if (w <= h)
        {
        windowWidth = 100;
        windowHeight = 100 / aspectRatio;
        glOrtho (-100.0, 100.0, -windowHeight, windowHeight, 1.0, -1.0);
        }
    else
        {
        windowWidth = 100 * aspectRatio;
        windowHeight = 100;
        glOrtho (-windowWidth, windowWidth, -100.0, 100.0, 1.0, -1.0);
        }

    glMatrixMode(GL_MODELVIEW);
    glLoadIdentity();
```
This is under my reshape function.
[/LEFT]

---

### Post by Sockerdrickan on 2010-07-16
Perhaps there IS a problem with the texture. What value does the id hold?

---

### Post by Eragon0605 on 2010-07-16
The ID in my case is tex_2d, correct? If so, it starts out as one (or maybe zero, it moves to fast for me to see) and then every time the program loops it goes up one more.

EDIT: I confirmed it starts at 1.

---

### Post by Sockerdrickan on 2010-07-16
It's supposed to get one id and stay at that id, you are reloading the texture all of the time. Only load the texture once before entering a while loop.

---

### Post by Eragon0605 on 2010-07-16
Ah, ok. That's fixed. Now every time the program loops, the id number is 1. But I'm still getting that square with no texture applied. Oh, and I was looking around online and supposedly the drawing color needs to be white for the texture to display right. I did so, but no change (i mean, the square is white but still no texture).

EDIT: Oooh, here might be an interesting thing. I tried running a sample program from the openGL superbible, and guess what? Compiled fine, ran it, and no textures! According to the program, the textures load fine, but something is preventing it from displaying on the screen. On top of that, if I try to load a 3D application, like glest, the textures load fine!

---

### Post by Sockerdrickan on 2010-07-16
What video card / drivers are you on?

---

### Post by Eragon0605 on 2010-07-16
I have an nVidia GTX 260, with the very latest drivers, 256.35

---

### Post by Sockerdrickan on 2010-07-16
Cool. Well I guess I could check this out if you post the full source file so that I can compile it from here and come back with the solution.

---

### Post by Eragon0605 on 2010-07-16
Ok, here is the full source:
```

#include <GL/glut.h>
#include <SOIL.h>
#include <iostream>

//Sets jimmy's initial position and size.
//rsize equals half of jimmy's height and width
GLfloat x = 0.0f;
GLfloat y = 0.0f;
GLfloat rsize = 8;
int frames = 5, full = 0;
int i = 0;
//Sets the direction and velocity of jimmy at the program initialization
/*The value of these variables defines the amount of pixels along the standard Cartesian coordinate system
Jimmy moves. For example, setting xstep to -2.0f would mean that jimmy would move two pixels
in a certain amount of time defined by the frames variable. The frames variable dictates the amount of milliseconds inbetween each movement of the square.
That means that if frames = 2, I get 50 fps, and therefore 50 movements of jimmy in a second.*/
GLfloat xstep = 0.0f;
GLfloat ystep = 0.0f;

GLfloat windowWidth;
GLfloat windowHeight;

GLuint tex_2d;

void keycrap(unsigned char key, int x, int  y)
{
    switch (key)
    {
        //32 is the ASCII value of the space key
        case 32:
        xstep = 0.0f, ystep = 0.0f;
        break;

        //27 is the ASCII value of the ESC key
        case 27:
        exit(0);
        break;

        case 'f':
        if (full == 0)
        {
            glutFullScreen();
            full = 1;
        }
        else
        {
            glutReshapeWindow(800, 600);
            glutPositionWindow(320,150);
            full = 0;
        }
    }
}

void SpecialKeys(int key, int x, int y)
{
    switch (key)
    {
        case GLUT_KEY_RIGHT:
        xstep = 1.0f, ystep = 0.0f;
        break;

        case GLUT_KEY_LEFT:
        xstep = -1.0f, ystep = 0.0f;
        break;

        case GLUT_KEY_DOWN:
        xstep = 0.0f, ystep = -1.0f;
        break;

        case GLUT_KEY_UP:
        xstep = 0.0f, ystep = 1.0f;
        break;
    }

    glutPostRedisplay();
}

void RenderScene()
{
    //Clears the window with current clearing color
    glClear(GL_COLOR_BUFFER_BIT);

       //Sets current drawing color
       //NOTE: Values are in float format, so 1.0f is full intensity
    glColor3f(0.0f, 0.0f, 0.0f);

    //Draws a square/rectangle with above drawing color
    glRectf(x, y, x + rsize, y - rsize);

    glEnable(GL_TEXTURE_2D);

    glColor4f(1.0f, 1.0f, 1.0f, 1.0f);

    if (i == 0)
    {
    tex_2d = SOIL_load_OGL_texture
    (
        "circle.png",
        SOIL_LOAD_RGBA,
        SOIL_CREATE_NEW_ID,
        SOIL_FLAG_TEXTURE_RECTANGLE | SOIL_FLAG_NTSC_SAFE_RGB
    );
    i = 1;
    }

    glBindTexture(GL_TEXTURE_2D, tex_2d);

    glTexEnvf(GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_MODULATE);

    std::cout << tex_2d << std::endl;

    glBegin(GL_POLYGON);
        glTexCoord2f(0.0, 0.0); glVertex2f(-8.0f, -8.0f);
        glTexCoord2f(1.0, 0.0); glVertex2f(8.0f, -8.0f);
        glTexCoord2f(1.0, 1.0); glVertex2f(8.0f, 8.0f);
        glTexCoord2f(0.0, 1.0); glVertex2f(-8.0f, 8.0f);
    glEnd();

    //Swaps the onscreen and offscreen buffers and flushes them
    glutSwapBuffers();
    glDisable(GL_TEXTURE_2D);
}

void TimerFunction(int value)
{
    //Makes Jimmy bounce when he hits the right or left window
    if(x > windowWidth-rsize || x < -windowWidth)
        xstep = -xstep;

    //Makes Jimmy bounce when he hits the top or bottom window
    if(y > windowHeight || y < -windowHeight + rsize)
        ystep = -ystep;

    //Moves the square
    x += xstep;
    y += ystep;

    //Checks the window size to make sure that Jimmy is actually bouncing off the edges of the screen
    if(x > (windowWidth-rsize + xstep))
        x = windowWidth-rsize-1;
    else if(x < -(windowWidth + xstep))
        x = -windowWidth -1;

    if(y > (windowHeight + ystep))
        y = windowHeight-1;
    else if(y < -(windowHeight - rsize + ystep))
        y = -windowHeight + rsize - 1;



     //Redraws the scene with all changes above
    glutPostRedisplay();
    glutTimerFunc(frames,TimerFunction, 1);
}

void SetupRC(void)
{
    //Sets the clear color. Again, the values are in RGBA float format
    glClearColor(0.0f, 0.8f, 0.0f, 1.0f);

    glTexEnvi(GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_MODULATE);
    glEnable(GL_TEXTURE_2D);
}

void ChangeSize(int w, int h)
{
    GLfloat aspectRatio;

    //Prevents a divid by zero. We wouldn't want that, now, would we.
    if(h == 0)
        h = 1;

    //Makes sure that the OpenGL viewport fills the whole screen
    glViewport(0, 0, w, h);

    //Resets the coordinate system so that the center of the window is (0,0,0) Cartesian x,y,z style
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();

    //Sets the clipping volume to the dimensions of the window, including depth ^_^
    aspectRatio = (GLfloat)w / (GLfloat)h;
    if (w <= h)
        {
        windowWidth = 100;
        windowHeight = 100 / aspectRatio;
        glOrtho (-100.0, 100.0, -windowHeight, windowHeight, 1.0, -1.0);
        }
    else
        {
        windowWidth = 100 * aspectRatio;
        windowHeight = 100;
        glOrtho (-windowWidth, windowWidth, -100.0, 100.0, 1.0, -1.0);
        }

    glMatrixMode(GL_MODELVIEW);
    glLoadIdentity();
}


//Actually opens the window, initializes all the functions I made, and throws it all into a loop. Hooray!
int main(int argc, char* argv[])
{
        glutInit(&argc, argv);
        glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA);
        glutInitWindowSize(800,600);
        glutCreateWindow("Get the Burger 3 - OpenGL");
        glutPositionWindow(320,150);
        glutIgnoreKeyRepeat(1);
        glutSpecialFunc(SpecialKeys);
        glutKeyboardFunc(keycrap);
        glutDisplayFunc(RenderScene);
        glutReshapeFunc(ChangeSize);
        glutTimerFunc(33, TimerFunction, 1);
        SetupRC();
        glutMainLoop();

    return 0;
}
```

---

### Post by nrs on 2010-07-17
```

 95 
 96     if (i == 0)
 97     {
 98             SDL_Surface *temp;
 99             temp = IMG_Load("playtheory.bmp");
100             if(!temp) {
101                     std::cout << SDL_GetError() << "\n";
102                     return ; 
103             }
104 
105             glGenTextures(1, &tex_2d);
106             glBindTexture(GL_TEXTURE_2D, tex_2d);
107             glTexImage2D(GL_TEXTURE_2D, 0, 3, temp->w,
108                             temp->h, 0, GL_RGBA, GL_UNSIGNED_BYTE,
109                             temp->pixels);
110             glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
111             glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
112             
113             i = 1;
114             SDL_FreeSurface(temp);
115     }       
116     

```Works. So the problem has got to be how you're using soil, or your texture. 90% of the time when textures don't load for me it's because there's a problem with them instead of the code. Try making it a simple 24bit bmp. 

 I can't help you with any soil because I didn't even know what it was until I ran pacman -Qi. :P 

[FONT=monospace]Your indentation for soil_load_ogl_texture threw me off for a moment. :P[/FONT]

---

### Post by Sockerdrickan on 2010-07-17
> **Eragon0605 said:**
> Ok, here is the full source:
```
code
```

Ok I located the problem

```

    tex_2d = SOIL_load_OGL_texture
    (
        "circle.png",
        SOIL_LOAD_RGBA,
        SOIL_CREATE_NEW_ID,
        **SOIL_FLAG_TEXTURE_RECTANGLE **| SOIL_FLAG_NTSC_SAFE_RGB
    );

```

vs working:

```

    tex_2d = SOIL_load_OGL_texture
    (
        "circle.png",
        SOIL_LOAD_RGBA,
        SOIL_CREATE_NEW_ID,
        SOIL_FLAG_NTSC_SAFE_RGB
    );

```

Always experiment with your code if there is an unknown problem

---

### Post by Eragon0605 on 2010-07-17
Ah, removing the SOIL_FLAG_TEXTURE_RECTANGLE fixed the problem. Many thanks for all the time and effort you put into solving my problem.

---


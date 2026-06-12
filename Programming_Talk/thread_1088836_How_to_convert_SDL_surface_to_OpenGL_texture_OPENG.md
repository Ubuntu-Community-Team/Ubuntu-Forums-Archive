---
title: "How to convert SDL surface to OpenGL texture? *OPENGL GURUS READ THIS*"
date: 2009-03-06
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-03-06
So far I got this. (it's plain C, not PHP or C++)
```

typedef struct _glTex
{
    GLuint data;
    unsigned int width, height;
} glTex;

```

```

// convert SDL surface to OpenGL texture
glTex surfaceToTexture( SDL_Surface *surf )
{
    glTex texture;
    
    // save texture size, this might be needed later
    texture.width = surf->w;
    texture.height = surf->h;
    
    // color format of image
    GLenum SourceFormat = GL_BGR;
    
    if ( surf->flags & SDL_SRCALPHA )
        // for some reason bmps activate this, when they don't have alpha channel, WTF?
        SourceFormat = GL_RGBA;
    else if ( surf->format->BitsPerPixel == 8 )
        SourceFormat = GL_COLOR_INDEX;
    
    // get an empty slot from texture memory
    glGenTextures( 1, &texture.data );
    
    // Typical Texture Generation Using Data From The Bitmap
    glBindTexture( GL_TEXTURE_2D, texture.data );

    // Generate The Texture
    glTexImage2D( GL_TEXTURE_2D, 0, surf->format->BytesPerPixel, \
    surf->w, surf->h, 0, SourceFormat, GL_UNSIGNED_BYTE, surf->pixels );
    
    // Linear Filtering, 2D doesn't need very good filters I guess
    glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR );
    glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR );

    // wrapping
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
    
    return texture;
}

```

It works fine with PNG, including alpha channel.  But most other formats don't work. All of them got either colors inverted/twisted, 

or then they are something absolutely random, which cannot be recognized. TGA works with GL_BGRA, but I don't know how to

recognize if its TGA. And I have no clue about the rest of image formats.. So the problem is, how can the correct pixel format be selected?

---

### Post by cb951303 on 2009-03-06
from an old project of mine

```

SDL_Surface *surface;
GLenum textureFormat;
GLuint texture;

.
.
.

    /* Set the color mode */
    switch (surface->format->BytesPerPixel) {
        case 4:
            if (SDL_BYTEORDER == SDL_BIG_ENDIAN)
                textureFormat = GL_BGRA;
            else
                textureFormat = GL_RGBA;
            break;

        case 3:
            if (SDL_BYTEORDER == SDL_BIG_ENDIAN)
                textureFormat = GL_BGR;
            else
                textureFormat = GL_RGB;
            break;
    }

    /* Genarate texture */
    glGenTextures(1, &texture);
    glBindTexture(GL_TEXTURE_2D, texture);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_NEAREST);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
    glTexImage2D(GL_TEXTURE_2D, 0, surface->format->BytesPerPixel, surface->w,
    surface->h, 0, textureFormat, GL_UNSIGNED_BYTE, surface->pixels);

.
.
.

```

---

### Post by crazyfuturamanoob on 2009-03-06
> **cb951303 said:**
> from an old project of mine

```

SDL_Surface *surface;
GLenum textureFormat;
GLuint texture;

.
.
.

    /* Set the color mode */
    switch (surface->format->BytesPerPixel) {
        case 4:
            if (SDL_BYTEORDER == SDL_BIG_ENDIAN)
                textureFormat = GL_BGRA;
            else
                textureFormat = GL_RGBA;
            break;

        case 3:
            if (SDL_BYTEORDER == SDL_BIG_ENDIAN)
                textureFormat = GL_BGR;
            else
                textureFormat = GL_RGB;
            break;
    }

    /* Genarate texture */
    glGenTextures(1, &texture);
    glBindTexture(GL_TEXTURE_2D, texture);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_NEAREST);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
    glTexImage2D(GL_TEXTURE_2D, 0, surface->format->BytesPerPixel, surface->w,
    surface->h, 0, textureFormat, GL_UNSIGNED_BYTE, surface->pixels);

.
.
.

```

I tried some formats and it doesn't work any better, although it the code looks better.

[list]
[*]GIF - completely white texture
[*]BMP - red and blue inverted
[*]TGA - same as above
[*]PNG - works ok
[/list]

All PNG, TGA and BMP get GL_BGRA, which messes it up if its not PNG. Why!? I though you can't save alpha channels in BMP.

---

### Post by cb951303 on 2009-03-06
> **crazyfuturamanoob said:**
> I tried some formats and it doesn't work any better, although it the code looks better.

[list]
[*]GIF - completely white texture
[*]BMP - red and blue inverted
[*]TGA - same as above
[*]PNG - works ok
[/list]

All PNG, TGA and BMP get GL_BGRA, which messes it up if its not PNG. Why!? I though you can't save alpha channels in BMP.

BMPs can't have alpha. you're right. I used this piece of code for PNG and JPG, it was working okay. Are you sure your test image files are ok?

EDIT: Lookin through the files, apparently I used it for TGA too.

---

### Post by crazyfuturamanoob on 2009-03-06
Yeah, the test files are OK. I made them with GIMP, and Ubuntu's default image viewers read them without a problem.

And right-click -> Properties -> Type shows correctly BMP/PNG/TGA/GIF. (right-click thing doesn't depend on extension, right?)

And if I use plain SDL to render the loaded images, without OpenGL, they show up correctly. So the files must be ok.

I also noticed that my code shows BMP as total mess, but yours shows it just red and blue inverted.

---

### Post by cb951303 on 2009-03-06
> **crazyfuturamanoob said:**
> Yeah, the test files are OK. I made them with GIMP, and Ubuntu's default image viewers read them without a problem.

And right-click -> Properties -> Type shows correctly BMP/PNG/TGA/GIF. (right-click thing doesn't depend on extension, right?)

And if I use plain SDL to render the loaded images, without OpenGL, they show up correctly. So the files must be ok.

I also noticed that my code shows BMP as total mess, but yours shows it just red and blue inverted.

:( it looks pretty straightforward. I don't know why it doesn't work. I'll look into it when I get home

---

### Post by crazyfuturamanoob on 2009-03-06
I tested JPG as well, it works OK.

For now, I'll be happy with PNG and JPG.

But it would be nice if other formats worked.

---

### Post by slavik on 2009-03-06
there's an SDL_image library that can load images for you. :)

---

### Post by cb951303 on 2009-03-06
BTW, are your image file dimensions power of 2? In opengl texture dimensions need to be power of 2 like 512x256 etc.

---

### Post by hessiess on 2009-03-06
If PNG works, then convert all of your files into PNG format. sticking to one format only is simpler than handling multiple formats. PNG is a better format anyway, being lossless(unlike jpg), supports alpha channel(unlike jpg and BMP) and often achieves a higher compression ratio than the other lossless formats.

If you must use a lossy format, go with something supported natively by OpenGL, which would save disk space AND ram.

---

### Post by cb951303 on 2009-03-06
ok, I had a chance to look at this and it may be a bug. First of all, since GIF is a 8-bit indexed image type lets assume there is another reason its not working. 

now, when it comes to PNG and JPG there is nothing wrong. *But* TGA and BMP are reversed. If you change the mode from BGR to RGB manually you will see that BMP and TGA works perfectly too.

Here is the code I tested. I created a 128x128 24 bit (no alpha) image in all above formats to test (see attach.)

[php]
#include <stdio.h>
#include <stdlib.h>
#include <SDL/SDL.h>
#include <SDL/SDL_opengl.h>
#include <SDL/SDL_image.h>

#define WIDTH 800
#define HEIGHT 600

GLuint LoadTexture(char *filename, int *textw, int *texth)
{
    SDL_Surface *surface;
    GLenum textureFormat;
    GLuint texture;

    surface = IMG_Load(filename);
    if (!surface){
        return 0;
    }

    switch (surface->format->BytesPerPixel) {
        case 4:
            if (SDL_BYTEORDER == SDL_BIG_ENDIAN)
                textureFormat = GL_BGRA;
            else
                textureFormat = GL_RGBA;
            break;

        case 3:
            if (SDL_BYTEORDER == SDL_BIG_ENDIAN)
                textureFormat = GL_BGR;
            else
                textureFormat = GL_RGB;
            break;
    }

    *textw = surface->w;
    *texth = surface->h;

    glGenTextures(1, &texture);
    glBindTexture(GL_TEXTURE_2D, texture);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_NEAREST);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
    glTexImage2D(GL_TEXTURE_2D, 0, surface->format->BytesPerPixel, surface->w,
    surface->h, 0, textureFormat, GL_UNSIGNED_BYTE, surface->pixels);

    SDL_FreeSurface(surface);

    return texture;

}

void DrawTexture(int x, int y, GLuint textureid, int textw, int texth)
{
    glBindTexture(GL_TEXTURE_2D, textureid);
    glEnable(GL_TEXTURE_2D);

    glBegin(GL_QUADS);
        glTexCoord2i(0, 0);
        glVertex2f(x, y);

        glTexCoord2i(1, 0);
        glVertex2f(x + textw, y);

        glTexCoord2i(1, 1);
        glVertex2f(x + textw, y + texth);

        glTexCoord2i(0, 1);
        glVertex2f(x, y + texth);
    glEnd();

    glDisable(GL_TEXTURE_2D);
}

void Enable2D()
{
    glMatrixMode(GL_PROJECTION);
    glPushMatrix();
    glLoadIdentity();
    glOrtho(0, WIDTH, HEIGHT, 0, -1, 1);
    glDisable(GL_DEPTH_TEST);
    glMatrixMode(GL_MODELVIEW);
    glPushMatrix();
    glLoadIdentity();
}

void Disable2D()
{
    glMatrixMode(GL_PROJECTION);
    glPopMatrix();
    glMatrixMode(GL_MODELVIEW);
    glPopMatrix();
    glEnable(GL_DEPTH_TEST);
}

int main( int argc, char **argv )
{
    const SDL_VideoInfo* video;
    SDL_Event e;
    GLuint texture;
    int textw, texth;

    if(SDL_Init(SDL_INIT_VIDEO) < 0)
    {
        fprintf(stderr, "Couldn't initialize SDL: %s\n", SDL_GetError());
        exit(1);
    }

    atexit(SDL_Quit);

    video = SDL_GetVideoInfo();
    if(video == NULL)
    {
        fprintf(stderr, "Couldn't get video information: %s\n", SDL_GetError());
        exit(1);
    }

    SDL_GL_SetAttribute(SDL_GL_RED_SIZE, 5);
    SDL_GL_SetAttribute(SDL_GL_GREEN_SIZE, 5);
    SDL_GL_SetAttribute(SDL_GL_BLUE_SIZE, 5);
    SDL_GL_SetAttribute(SDL_GL_DEPTH_SIZE, 16);
    SDL_GL_SetAttribute(SDL_GL_DOUBLEBUFFER, 1);

    if(SDL_SetVideoMode(WIDTH, HEIGHT, video->vfmt->BitsPerPixel, SDL_OPENGL) == 0 )
    {
        fprintf(stderr, "Couldn't set video mode: %s\n", SDL_GetError());
        exit(1);
    }

    texture = LoadTexture("testImage.png", &textw, &texth);

    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glLoadIdentity();

    while(!SDL_PollEvent(&e) || e.type!=2)
    {
        Enable2D();
            DrawTexture(0, 0, texture, textw, texth);
        Disable2D();

        SDL_GL_SwapBuffers();
    }
}
[/php]

when you change this:
[php]
        case 3:
            if (SDL_BYTEORDER == SDL_BIG_ENDIAN)
[/php]
to this:
[php]     
   case 3:
            if (SDL_BYTEORDER != SDL_BIG_ENDIAN)
[/php]

TGA and BMP starts working but this time PNG and JPG gets reversed. I guess you can throw some conditions according to the file extension and make them all work but still the current behavior is weird.

---

### Post by Gordon Bennett on 2009-03-06
You pretty much figured it out yourself already :)

As you can see, it's due to the pixel packing format output of the various file formats.  It's like the difference between left-hand drive and right-hand-drive cars - they do the same job, in a different way!

If you want to be able to use a multitude of file formats, you'll have to process by filetype.  There's some cool colour-space converters in Video4Linux you can use.

---

### Post by crazyfuturamanoob on 2009-03-07
So the only way around seems to be to check the file extension from filename when loading the file.

> **slavik said:**
> there's an SDL_image library that can load images for you. :)

SDL_image loads images into SDL surfaces, not OpenGL textures.

> **cb951303 said:**
> BTW, are your image file dimensions power of 2? In opengl texture dimensions need to be power of 2 like 512x256 etc.

Yes, this test image I use is 128x128. But I think that limitation is removed nowadays.

---

### Post by cb951303 on 2009-03-07
> **crazyfuturamanoob said:**
> 
Yes, this test image I use is 128x128. But I think that limitation is removed nowadays.

Are you sure? You can use mipmaps to use non-power-of-2 textures but I didn't know the limitation is removed :confused:

---

### Post by crazyfuturamanoob on 2009-03-07
I'm not sure. 

I googled and found out it's an extension which does it:
> 
OpenGL texturing is limited to images with power-of-two dimensions
and an optional 1-texel border.  The ARB_texture_rectangle extension
adds a new texture target that supports 2D textures without requiring
power-of-two dimensions.


For now, I'll just be happy with PNG working.

---

### Post by cb951303 on 2009-03-07
> **crazyfuturamanoob said:**
> I'm not sure. 

I googled and found out it's an extension which does it:


For now, I'll just be happy with PNG working.

I didn't know about that. and it only requires opengl 1.1, I'll use it if I ever do games again :D

---

### Post by Gordon Bennett on 2009-03-07
Non power-of-two texture support depends on the driver version and the windowing system - for example, in my app I am able to use non-power-of-two textures in all texture modes by default (nVidia driver, Ubuntu 8.10 using GtkGLExt).  It's a 7800GTX which has driver + hardware support for it.

There isn't a significant performance hit in most modern cards as they have advanced databurst transfer logic in them.

If you want to be sure you have it enabled, you can check for and use:

GL_ARB_texture_non_power_of_two

Any card/driver that's compatible with OpenGL 1.4 (and above) will be able to do this.  Here's an overview from an [OpenGL capabilities list]("http://developer.apple.com/graphicsimaging/opengl/capabilities/") - you can see that cards as old as Radeon 9600 and GeForce 6600 support it.

If you are running on a very, very old gfx card, you can use several techniques to have optimal performance; I assume you have a relatively modern card though :)

---

### Post by crazyfuturamanoob on 2009-03-07
> **Gordon Bennett said:**
> Non power-of-two texture support depends on the driver version and the windowing system - for example, in my app I am able to use non-power-of-two textures in all texture modes by default (nVidia driver, Ubuntu 8.10 using GtkGLExt).  It's a 7800GTX which has driver + hardware support for it.

There isn't a significant performance hit in most modern cards as they have advanced databurst transfer logic in them.

If you want to be sure you have it enabled, you can check for and use:

GL_ARB_texture_non_power_of_two

Any card/driver that's compatible with OpenGL 1.4 (and above) will be able to do this.  Here's an overview from an [OpenGL capabilities list]("http://developer.apple.com/graphicsimaging/opengl/capabilities/") - you can see that cards as old as Radeon 9600 and GeForce 6600 support it.

If you are running on a very, very old gfx card, you can use several techniques to have optimal performance; I assume you have a relatively modern card though :)

So non-powers of 2 textures might work without that extension? At least they do on my GeForce 8600 GS.

---

### Post by slavik on 2009-03-07
crazyfuturamanoob, You are correct, SDL_image loads things into an SDL_Surface, but then it's very easy to give that info to OpenGL SDL_Surface->pixels.

As for power of 2 limitation. It is not a limitation anymore. It was a limitation in an older version of OpenGL, but it isn't since OpenGL 1.5.

---

### Post by crazyfuturamanoob on 2009-03-07
> **slavik said:**
> crazyfuturamanoob, You are correct, SDL_image loads things into an SDL_Surface, but then it's very easy to give that info to OpenGL SDL_Surface->pixels.

Yeah, but the problem was the correct pixel format, as you see.

---

### Post by slavik on 2009-03-07
> **crazyfuturamanoob said:**
> Yeah, but the problem was the correct pixel format, as you see.
yea ... extra post processing of the data is required. :(

---

### Post by Gordon Bennett on 2009-03-07
> **crazyfuturamanoob said:**
> So non-powers of 2 textures might work without that extension? At least they do on my GeForce 8600 GS.

If your app relies on it, always check for the feature!  It's good practice to test for a given extension to the original spec even though you can safely assume it's there - it will help avoid crash-and-burn situations when your app depends on its presence.

Or, you can set a minimum spec for your app: 'requires an OpenGL 1.4 (or greater) capable card'.

---

### Post by Gordon Bennett on 2009-03-07
Edit, from [OpenGL.org's notes]("http://www.opengl.org/wiki/NPOT_Textures"):

**  OpenGL 2.0 and GL_ARB_texture_non_power_of_two**

With GL 2.0, you can make textures of any type (2D, 3D, cubemap), with any dimension, any filter mode, mipmaps, anisotropy, any wrap mode. It may however run in software mode. If GL_ARB_texture_non_power_of_two is present, it should always run in hw mode. GL_ARB_texture_non_power_of_two is thus an indicator extension.
If you don't have GL_ARB_texture_non_power_of_two, then you can make NPOT texture, just that follow the same limitation as for GL_ARB_texture_rectangle (no mipmaps, GL_CLAMP_TO_EDGE, etc) and it will be hw accelerated.


So basically, if the card has OpenGL 2.0 or above and has GL_ARB_texture_non_power_of_two defined, you have guaranteed hardware-accelerated arbitrary-sized textures without the powers-of-two restriction.

---


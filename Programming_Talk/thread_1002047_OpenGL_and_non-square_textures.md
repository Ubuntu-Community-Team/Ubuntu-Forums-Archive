---
title: "OpenGL and non-square textures"
date: 2008-12-04
forum: Programming Talk
---

### Post by mee.six on 2008-12-04
Hello,

I'm new to OpenGL, and can't create a non-square texture. Can anyone help? 

best regards,
mee

---

### Post by Sydius on 2008-12-04
As in rectangular, 1-dimensional, 3-dimensional, or something else?

---

### Post by slavik on 2008-12-05
if you are talking about a shape that does not fit a quad (circle?), you can map it onto a quad, but made the parts of the textures that are supposed to be invisible transparent.

please explain in a little more detail what you are hoping to achieve.

---

### Post by mee.six on 2008-12-05
Thanks for such a fast reaction!

I'm doing an augmented reality app, and my aim is to put some image over a marker in webcam's picture at the right angle. Everything works great, except the fact, that I'm using a texture (a ppm file) only in specifiled size. A side length of texture can be only power of two (2^n). When I use other image size, I only get a white square. 

Here is the code:
```

glGenTextures(1, &pgm_texID);
glBindTexture(GL_TEXTURE_2D, pgm_texID);		
glTexParameteri(GL_TEXTURE_2D,GL_TEXTURE_MAG_FILTER,GL_LINEAR);					
glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, width, height, 0, GL_RGB, GL_UNSIGNED_BYTE,texpgm);


```
texpgm - is a texture read from ppm file.

And then something like that:
```

glBindTexture(GL_TEXTURE_2D, camera_texID);
glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, 1024, 1024, 0, GL_BGR_EXT, GL_UNSIGNED_BYTE,cam_tex_img);

glutPostRedisplay();

```

---

### Post by Kazade on 2008-12-05
OK a couple things. Firstly are you definitely calling glEnable(GL_TEXTURE_2D)?

Secondly:

```

glBindTexture(GL_TEXTURE_2D, camera_texID);
glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, 1024, 1024, 0, GL_BGR_EXT, GL_UNSIGNED_BYTE,cam_tex_img);

```

might need to be changed to:

```

glBindTexture(GL_TEXTURE_2D, camera_texID);
glTexParameteri(GL_TEXTURE_2D,GL_TEXTURE_MAG_FILTER,GL_LINEAR);		
glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, 1024, 1024, 0, GL_BGR_EXT, GL_UNSIGNED_BYTE,cam_tex_img);

```

As you aren't using mipmaps, and the default MAG_FILTER is GL_MIPMAP_LINEAR (IIRC).

---

### Post by mee.six on 2008-12-06
ok, thanks, it probably made my code better, but texture is still white :( and yes, I'm definitely calling glEnable :)

---

### Post by Delever on 2008-12-06
You know, you CAN use different sizes for edges, like 1024 for width and 2048 for height.

If your image is, for example, 912 x 610, resize it with some graphics program to 1024 x 512 (or 1024 x 1024), and use it. Make sure the geometry you are mapping texture into is correct size (912 x 610), and you are done.

---

### Post by DougB1958 on 2008-12-06
> **mee.six said:**
> ...A side length of texture can be only power of two (2^n). When I use other image size, I only get a white square.

That sides must be a power of 2 is a design limit of OpenGL prior to version 2.0. So if your problem is that your textures map correctly when their sides are a power of 2 in length, and come out white otherwise, and you're using a pre-2.0 version of OpenGL, that may be the cause. (And the solution would be to either live with powers of 2 or upgrade your OpenGL.)

---

### Post by Delever on 2008-12-06
> **DougB1958 said:**
> That sides must be a power of 2 is a design limit of OpenGL prior to version 2.0. So if your problem is that your textures map correctly when their sides are a power of 2 in length, and come out white otherwise, and you're using a pre-2.0 version of OpenGL, that may be the cause. (And the solution would be to either live with powers of 2 or upgrade your OpenGL.)

I think it is mainly hardware limitation, though I am not sure.

---

### Post by snova on 2008-12-06
> **Delever said:**
> I think it is mainly hardware limitation, though I am not sure.

Not so much a limitation, I think, but because it is faster that way.

---

### Post by crazyfuturamanoob on 2008-12-07
Some time ago, I wrote a function to load almost any image format (including alpha channel) into an OpenGL texture.

Hopefully someone finds this useful:
```

#include <stdio.h>
#include <GL/gl.h>
#include <GL/glu.h>
#include "SDL.h"
#include "SDL_image.h"

struct glTEX
{
    GLuint data;
    int width, height;
};

struct glTEX LoadTexture( char filename[] )
{
    /* create storage space for texture */
    SDL_Surface *TexIMG;
    struct glTEX texture;
    
    /* Load The Bitmap, Check For Errors, If Bitmap's Not Found Quit */
    if ( (TexIMG = IMG_Load(filename)) )
    {
        /* save texture size, this might be needed to draw the texture centered */
        texture.width = TexIMG->w;
        texture.height = TexIMG->h;
        
        /* color format of image */
        GLenum SourceFormat = GL_BGR;
        if (TexIMG->flags&SDL_SRCALPHA)
                SourceFormat=GL_RGBA;
        else if (TexIMG->format->BitsPerPixel==8)
                SourceFormat=GL_COLOR_INDEX;
        
        /* Create The Texture */
        glGenTextures( 1, &texture.data );

        /* Typical Texture Generation Using Data From The Bitmap */
        glBindTexture( GL_TEXTURE_2D, texture.data );

        /* Generate The Texture */
        glTexImage2D( GL_TEXTURE_2D, 0, TexIMG->format->BytesPerPixel, 
                      TexIMG->w, TexIMG->h, 0, SourceFormat,
                      GL_UNSIGNED_BYTE, TexIMG->pixels );

        /* Linear Filtering */
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR );
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR );
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
        
    }
    else
    {
        /* something went wrong when loading texture, report error message */
        printf( "Failed to load texture %s, reason: %s\n", filename, IMG_GetError() );
    }

    /* Free up any memory we may have used */
    if ( TexIMG )
	    SDL_FreeSurface( TexIMG );
    
    return texture;
}


```

Remember to link SDL when compiling.

Example of usage:

```

struct glTEX mytexture = LoadTexture("data/file.png");

glBindTexture( GL_TEXTURE_2D, mytexture->data )

glBegin( GL_SOMETHING );
glVertex2f( ... );
...
glEnd();

```

Works with multiple textures, works with alpha channels, and many different file types SDL supports.

---

### Post by Sockerdrickan on 2008-12-07
We were talking about non-square textures

---

### Post by tageiru on 2008-12-07
use GL_TEXTURE_RECTANGLE_ARB instead of GL_TEXTURE_2D.

It supports textures of any dimension, but keep in mind that rectangular textures can't be used with mipmap filtering and their UV coordinates need to be specified in pixels instead of being clamped between 0 and 1.

---

### Post by mee.six on 2008-12-08
> **Delever said:**
> You know, you CAN use different sizes for edges, like 1024 for width and 2048 for height.

If your image is, for example, 912 x 610, resize it with some graphics program to 1024 x 512 (or 1024 x 1024), and use it. Make sure the geometry you are mapping texture into is correct size (912 x 610), and you are done.

I know, it is the easiest way, but I need to render any image user wants, I can't force him to use any dimensions and in other hand, I can resize image right in my app, but stretching or cropping isn't appropriate.

> **DougB1958 said:**
> That sides must be a power of 2 is a design limit of OpenGL prior to version 2.0. So if your problem is that your textures map correctly when their sides are a power of 2 in length, and come out white otherwise, and you're using a pre-2.0 version of OpenGL, that may be the cause. (And the solution would be to either live with powers of 2 or upgrade your OpenGL.)
Oh... that's more interesting. Should I upgrade the code, or just openGL's libraries?

---

### Post by Kazade on 2008-12-08
> **tageiru said:**
> use GL_TEXTURE_RECTANGLE_ARB instead of GL_TEXTURE_2D.

It supports textures of any dimension, but keep in mind that rectangular textures can't be used with mipmap filtering and their UV coordinates need to be specified in pixels instead of being clamped between 0 and 1.

This is not the best way to go because of the non-normalized coordinates. Instead use the [non-power of two extension]("http://www.opengl.org/registry/specs/ARB/texture_non_power_of_two.txt") which keeps the standard normalized coordinates and also supports mipmaps. Or just generate mipmaps with gluBuild2DMipmaps() which will take any size texture as input.

---

### Post by mee.six on 2008-12-08
Actually I don't need mipmaping, so thanks, I'll try this littble bit later.

---

### Post by crazyfuturamanoob on 2008-12-08
> **tageiru said:**
> use GL_TEXTURE_RECTANGLE_ARB instead of GL_TEXTURE_2D.

It supports textures of any dimension, but keep in mind that rectangular textures can't be used with mipmap filtering and their UV coordinates need to be specified in pixels instead of being clamped between 0 and 1.

What are you talking about?

I have tested that code and I'm all the time clamping the texture coords between 1 and 0 with glTexCoord2f and it works. 

No problem with it. 

Actually I don't even know how to set the texture coords in pixels lol :D

---

### Post by Kazade on 2008-12-08
> **crazyfuturamanoob said:**
> What are you talking about?

I have tested that code and I'm all the time clamping the texture coords between 1 and 0 with glTexCoord2f and it works. 

No problem with it. 

Actually I don't even know how to set the texture coords in pixels lol :D

I don't know what you are using but you aren't using the [GL_TEXTURE_RECTANGLE_ARB extension]("http://www.opengl.org/registry/specs/ARB/texture_rectangle.txt") which specifically says:

    "NPOTS textures are accessed by dimension-dependent (aka
     non-normalized) texture coordinates.  So instead of thinking of
     the texture image lying in a [0..1]x[0..1] range, the NPOTS texture
     image lies in a [0..w]x[0..h] range."

---

### Post by crazyfuturamanoob on 2008-12-08
> **Kazade said:**
> I don't know what you are using but you aren't using the [GL_TEXTURE_RECTANGLE_ARB extension]("http://www.opengl.org/registry/specs/ARB/texture_rectangle.txt") which specifically says:

    "NPOTS textures are accessed by dimension-dependent (aka
     non-normalized) texture coordinates.  So instead of thinking of
     the texture image lying in a [0..1]x[0..1] range, the NPOTS texture
     image lies in a [0..w]x[0..h] range."

But it works. What's the matter then?

Can't it be used with 'non-square' textures?

There isn't any image format which can hold a non-rectangular area. Every image is a rectangle.

So I suggest OP wants to have a normal, rectangular texture, with alpha channel, with the actual image in the middle, and all surroundings transparent.
It doesn't look a square then.


Or maybe I misunderstood something?

---

### Post by mee.six on 2008-12-08
It's sad, but I have problem with GL_TEXTURE_RECTANGLE_ARB. It's just an undeclared identifier. Can I install it, or update headers or something?

---

### Post by Kazade on 2008-12-09
Make sure you are including the latest glext.h which can be found on the OpenGL registry at [http://www.opengl.org/registry/](http://www.opengl.org/registry/)

There seems to be a bit of confusion in this thread in regards to non-square textures vs non power of two textures.

OpenGL has always allowed for non-square textures but the length of the side used to be limited to powers of two for efficiency reasons. When the time came to remove this restriction two competing extensions were released: the texture rectangle extension and the non power of two extension. 

The texture rectangle extension allowed an entirely new target (as opposed to GL_TEXTURE_2D, GL_TEXTURE_3D etc.) which allowed use of any size texture but the texture coordinates had to be given in texels rather than normalized coordinates. 

A little later the non-power of two (NPOT) extension simply removed the restriction from the normal texture targets. At this point you could simply use any size texture and everything would continue working.

I would recommend using the NPOT extension over the texture rectangle one because you are basically using a special case for loading a particular texture as the target and texture coordinates need to be different.

---

### Post by mee.six on 2008-12-09
> **Kazade said:**
> Make sure you are including the latest glext.h which can be found on the OpenGL registry at [http://www.opengl.org/registry/](http://www.opengl.org/registry/)

There seems to be a bit of confusion in this thread in regards to non-square textures vs non power of two textures.

OpenGL has always allowed for non-square textures but the length of the side used to be limited to powers of two for efficiency reasons. When the time came to remove this restriction two competing extensions were released: the texture rectangle extension and the non power of two extension. 

The texture rectangle extension allowed an entirely new target (as opposed to GL_TEXTURE_2D, GL_TEXTURE_3D etc.) which allowed use of any size texture but the texture coordinates had to be given in texels rather than normalized coordinates. 

A little later the non-power of two (NPOT) extension simply removed the restriction from the normal texture targets. At this point you could simply use any size texture and everything would continue working.

I would recommend using the NPOT extension over the texture rectangle one because you are basically using a special case for loading a particular texture as the target and texture coordinates need to be different.

Ok, thanks, but how can I use this extension? glEnable(NPOT) or something?

---

### Post by Kazade on 2008-12-09
> **mee.six said:**
> Ok, thanks, but how can I use this extension? glEnable(NPOT) or something?

It should just come for free if your graphics card driver supports it (as in you just load the texture and it should work). If your card doesn't support it (which I'm guessing it doesn't as it's not working for you) then I guess you have no choice but to either:

a.) Fall back to GL_TEXTURE_RECTANGLE_ARB. Remember to glEnable() this and use it as the parameter to glTexImage*()

b.) Generate mipmaps for the image (if you use mipmapping, not only do you get a better quality rendering due to less artifacts, but gluBuild2DMipmaps function resizes your texture to a power of two automatically)

c.) Resize the texture manually in your program. A bit more tricky, you could pad the texture to the next largest power of two and do some clever texture coordinate generation to use only the portion of the texture that isn't padded.

I'd be surprised if your driver doesn't support the NPOT extension, try running: 
```

glxinfo | grep non_power 

```
and see if it's listed.

---


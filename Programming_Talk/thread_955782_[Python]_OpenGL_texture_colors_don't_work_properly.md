---
title: "[Python] OpenGL texture colors don't work properly, help needed!"
date: 2008-10-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-22
Look at the image, and you see, that the texture rendered with opengl looks odd. The colors aren't correct, and it looks blurry.
[IMG]http://img205.imageshack.us/img205/3769/gltestyx8.png[/IMG]
What I have done wrong? Why the colors aren't correct? What's wrong?

I made this function for creating textures from files:
```

def texture_from_file(filename, size):
    texture = GLuint()
    
    # open the file
    file = open(filename, 'r')
    
    width = size[0]
    height = size[1]
    
    # read the data in it and close the file
    data = file.read()
    file.close()
    
    glGenTextures(1, texture)
    
    OpenGL.GL.glBindTexture(GL_TEXTURE_2D, texture)
    
    # when texture area is small, bilinear filter the closest mipmap
    glTexParameterf( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER,GL_LINEAR_MIPMAP_NEAREST )
    
    # when texture area is large, bilinear filter the first mipmap
    glTexParameterf( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR )
    
    # build our texture mipmaps
    gluBuild2DMipmaps(GL_TEXTURE_2D, 3, width, height, GL_RGB, GL_UNSIGNED_BYTE, data)
    
    # return texture for user
    return texture
```

And I draw it with this:
```
glBindTexture(GL_TEXTURE_2D, tex)
glBegin(GL_QUADS)
glTexCoord2d(0, 0); glVertex2d(0, 0)
glTexCoord2d(1, 0); glVertex2d(40, 0)
glTexCoord2d(1, 1); glVertex2d(40, 40)
glTexCoord2d(0, 1); glVertex2d(0, 40)
glEnd()
```

That texture is a 40x40 bitmap:
[IMG]http://img147.imageshack.us/img147/4330/texud2.png[/IMG]

So what is the problem? Would somebody OpenGL expert tell me what I did wrong?

---

### Post by kupiakos on 2010-11-01
Here is a quick hint:
ALL textures must be in powers of two:
1x1, 2x2, 4x4, 8x8, 16x16, 32x32, 64x64, 128x128, 256x256, 512x512, 1024x1024, 2048x2048, 4096x4096... I think you get the idea :)

Since your texture is somewhere in the center of 64 and 32, you can either upscale or downscale your horse texture to either 64x64 or 32x32.

I'm trying to figure out how to create textures with PyOpenGL, but I do know the rules for textures from Game Maker.

Mind Helping Me with that? ;)

 - Kupiakos

---

### Post by curvedinfinity on 2010-11-02
You should be able to use different powers of two for height and width. Also, you can copy a non-power-of-two texture into the top left of a larger power of two buffer that you then load that onto the graphics card. Then you can multiply your UV coordinates based on the ratio of the real size and higher power of two:

```

int width = 40;
int power2 = originalWidth;

// Find next highest power of two
power2--;
for (int i=1; i<32; i<<=1)
   power2 = power2 | power2 >> i;
power2++;

// Copy width texture into power2 buffer

// find what to multiply against UVs
float widthRatio = width/(float)power2;

// Now load in UVs, multiplying them by that ratio

```

---


---
title: "[SOLVED] OpenGL texture help"
date: 2008-10-26
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-26
I want to use a bitmap as a texture, and to have the bitmap having alpha values. ANY image format is ok, as long as it works.
Alpha can be either color key or per-pixel alpha, no matter, as long as I can have part of the texture transparent.

How to do this? I am a total noob with opengl.

---

### Post by DougB1958 on 2008-10-26
I think you'll have to write (or find) your own code to read the image file. That's not part of OpenGL. An OpenGL texture is just an array of 3- or 4-byte RGB (or RGBA) colors, so that's the format you need to read the image into. In your case, it sounds like you'll use 4-byte RGBA.

See the OpenGL manual for the sequence of OpenGL functions you'll need to call to tell OpenGL how to use the texture once you've read it into an array.

(Sorry for the brevity here, I' short on time and my own OpenGL references are back at the office. But I hope this helps you get started.)

---

### Post by crazyfuturamanoob on 2008-10-27
Ok thanks anyway but I found a piece of code from some weird web site, that does the job.

(actually I had to heavily modify the code to get it working the way I want)

---

### Post by skullmunky on 2008-10-31
Hey, can you post your successful code?  This is one of the first big roadblocks that new opengl coders tend to hit, so the more good examples out there the better. :)

---

### Post by crazyfuturamanoob on 2008-10-31
Ok, but I noticed that code is a little malfunctioning. It isn't possible to have multiple textures.
```

class Texture(GLuint):
    """ A class for GLuint textures. """
    def __init__(self, filename):
        texture = GLuint()
        
        image = Image.open(filename)
        
        if len(image.getbands())!=4:
            image = image.convert("RGBA")
        
        self.size = image.size
        
        glGenTextures(1, texture)
        # apply the texture we just selected
        glBindTexture(GL_TEXTURE_2D, texture)
        
        # when texture area is small, bilinear filter the closest mipmap
        glTexParameterf( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER,GL_LINEAR_MIPMAP_NEAREST )
        
        # when texture area is large, bilinear filter the first mipmap
        glTexParameterf( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR )
        
        # generate texture
        self.string = image.tostring()
        self.value = gluBuild2DMipmaps(GL_TEXTURE_2D, 4, self.size[0], self.size[1], GL_RGBA, GL_UNSIGNED_BYTE, image.tostring())

```
I ment it to be like that *tex = Texture("folder/file.png")* and when using particular texture, 
then *glBindTexture(GL_TEXTURE_2D, tex)*, but for some reason it doesn't work. 

But recalling *gluBuild2DMipmaps* instead of *glBindtexture*, it will work, but it wastes a lot resources.
That code is python, and you also need to import Image to get it working.

Also, glColor4f and other color changing commands will not work properly with that texture thing.
The colors issued will be twisted with the current texture's palette.

---


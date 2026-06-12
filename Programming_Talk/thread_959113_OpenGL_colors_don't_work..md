---
title: "OpenGL colors don't work."
date: 2008-10-26
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-26
I want to use png as texture. And I want alpha values too.

I got a function to make a texture from a file. It is python, but pyOpenGL is probably same than OpenGL.
```

def texture_from_string(string, size, palette):
    texture = GLuint()
    
    width = size[0]
    height = size[1]
    
    data = string
    
    glGenTextures(1, texture)
    
    OpenGL.GL.glBindTexture(GL_TEXTURE_2D, texture)
    
    # when texture area is small, bilinear filter the closest mipmap
    glTexParameterf( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER,GL_LINEAR_MIPMAP_NEAREST )
    
    # when texture area is large, bilinear filter the first mipmap
    glTexParameterf( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR )
    
    # build our texture mipmaps
    gluBuild2DMipmaps(GL_TEXTURE_2D, 3, width, height, palette, GL_UNSIGNED_BYTE, data)
    
    # return texture for user
    return texture

def texture_from_file(filename, size, palette=GL_RGBA):
    file = open(filename, 'r')
    string = file.read()
    file.close()
    return texture_from_string(string, size, palette)
```
But when I try to draw a textured quad, I can't see the texture. And when I use glColor4f, I get colors seriously messed up. Like if I draw a green dot, it might be yellow or something else!
So the problem is probably with GL_RGBA or whatever it is called. With different values, I get different results. But I want to see my texture! Help!

---


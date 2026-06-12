---
title: "[OpenGL] PNG with alpha values as a texture?"
date: 2008-10-24
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-24
I want to have textures being partially transparent. And I want to use a png image with alpha values. How can this be done with OpenGL?

I wrote some code for loading textures. I have tested with bmps and pngs. Only bmps work. It might be the GL_BGR_SOMETHING that is the problem.
```
[color=#008000]**def**[/color] [color=#0000FF]texture_from_string[/color](string, size, palette[color=#666666]=[/color]GL_BGR_EXT):
    texture [color=#666666]=[/color] GLuint()
    
    width [color=#666666]=[/color] size[[color=#666666]0[/color]]
    height [color=#666666]=[/color] size[[color=#666666]1[/color]]
    
    data [color=#666666]=[/color] string
    
    glGenTextures([color=#666666]1[/color], texture)
    
    OpenGL[color=#666666].[/color]GL[color=#666666].[/color]glBindTexture(GL_TEXTURE_2D, texture)
    
    [color=#408080]*# when texture area is small, bilinear filter the closest mipmap*[/color]
    glTexParameterf( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER,GL_LINEAR_MIPMAP_NEAREST )
    
    [color=#408080]*# when texture area is large, bilinear filter the first mipmap*[/color]
    glTexParameterf( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR )
    
    [color=#408080]*# build our texture mipmaps*[/color]
    gluBuild2DMipmaps(GL_TEXTURE_2D, [color=#666666]3[/color], width, height, palette, GL_UNSIGNED_BYTE, data)
    
    [color=#408080]*# return texture for user*[/color]
    [color=#008000]**return**[/color] texture

[color=#008000]**def**[/color] [color=#0000FF]texture_from_file[/color](filename, size, palette[color=#666666]=[/color]GL_BGR_EXT):
    [color=#008000]file[/color] [color=#666666]=[/color] [color=#008000]open[/color](filename, [color=#BA2121]'r'[/color])
    string [color=#666666]=[/color] [color=#008000]file[/color][color=#666666].[/color]read()
    [color=#008000]file[/color][color=#666666].[/color]close()
    [color=#008000]**return**[/color] texture_from_string(string, size, palette)

```
NOTE: size argument is the width and height of the image, because I don't know how to autodetect it. Maybe with PIL but it really doesn't matter.

Anybody knows how to get that texture thing working with pngs? OH yes, and that is python above.

---


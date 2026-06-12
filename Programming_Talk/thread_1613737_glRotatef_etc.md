---
title: "glRotatef etc"
date: 2010-11-04
forum: Programming Talk
---

### Post by Devio on 2010-11-04
Is there a way to make a rotation just for one small string of glutBitmapCharacter?  At the moment my rotation does nothing until I minimise and maximise the window at which point everything in the window rotates around the origin but the small image itself wont rotate around it's centre!

I think I'm having problems with the Pop/PushMatrix commands or I just don't know where to call glRotatef.

```
void b(float x, float y, char *string, void *font)
  {
    glRasterPos2f(x, y);
    int len, i;    
    len = (int) strlen(string);
    for (i = 0; i < len; i++) 
    {
        glutBitmapCharacter(font, string[i]);
    }
    glRotatef(45,0.0,0.0,1.0);
    glPopMatrix();
}


void display(void)
{
    glClear(GL_COLOR_BUFFER_BIT) ;
    outline() ;
    a(-0.25,0.5,"RD", GLUT_BITMAP_TIMES_ROMAN_24) ;
    b(0.25,0.5,"RD", GLUT_BITMAP_TIMES_ROMAN_24) ;
    glutSwapBuffers() ;
}
```

These are the two parts of code in question, basically the idea is to have the b function to rotate 45 degrees anti-clockwise when I run the program.

Thanks for reading.

---

### Post by DougB1958 on 2010-11-04
Well, I don't do much with raster operations in OpenGL, but I'm pretty sure you need to call glRotatef **before** you call glutBitmapCharacter or glRasterPos2f, and if you're using glPopMatrix to remove the rotation, you need to call glPushMatrix before you call glRotatef.

---

### Post by Devio on 2010-11-04
I've tried that unfortunately, to no avail. :( That just seems to stop any rotations altogether.

Thanks for the reply :)

---

### Post by DanielWaterworth on 2010-11-05
I think gl pixel operations write directly to the video buffer. You'll need to put a texture on to a polygon for it to be affected by the transformation matrix AFAIK.

---

### Post by Devio on 2010-11-05
> **DanielWaterworth said:**
> I think gl pixel operations write directly to the video buffer. You'll need to put a texture on to a polygon for it to be affected by the transformation matrix AFAIK.

Right I see, in which case going down a different route, would glMultMatrix be more appropriate or does that follow the same idea? I have a feeling I'm gonna have to rethink my entire code this afternoon.

Thanks for the reply.

---

### Post by DanielWaterworth on 2010-11-05
I think (somebody correct me if I'm wrong) that raster operations are used for thing like rendering UIs, things that are stationary on the screen and aren't affected by lighting. It's simply writing to the video buffer.

operations like glrotatef, glscalef, glmultmatrixf, etc all change the current matrix (usually the modelview matrix). ie, glrotatef is the same as glmultmatrixf with a rotation matrix as an argument.

I've never done this before, but I think the process is:

create a frame buffer
bind it (this causes anything you render in opengl to go to the buffer rather than the screen).
render the text, (this is exactly the same as you did before),
unbind the frame buffer,
set the buffer as the texture,
set up the matrix, (glrotatef)
create a polygon (probably a square) with the texture,
swap buffers.

here's a tutorial an frame buffers,

[http://www.gamedev.net/reference/articles/article2331.asp](http://www.gamedev.net/reference/articles/article2331.asp)

---

### Post by Devio on 2010-11-05
Alright thanks for such an in depth reply! I'll have a look into that when I get home, hopefully I can get this sorted, I have to use glScalef later too so will come in useful then!

Thanks again!

---


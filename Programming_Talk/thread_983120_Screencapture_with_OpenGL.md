---
title: "Screencapture with OpenGL"
date: 2008-11-15
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-15
How to get screen capture with OpenGL and save into an existing texture on the fly?

I tried this:

```

GLuint ScreenCapture( )
{
    GLuint texture;
    
    glReadPixels( 0, 0, SCREEN_WIDTH, SCREEN_HEIGHT, GL_RGB, GL_UNSIGNED_INT, &texture );
    
    return texture;
}
```

Result: Freezes for a couple seconds before Segmentation Fault.

Oh yes, and language is C again.

---

### Post by skullmunky on 2008-11-22
```
texture
``` should be a malloc'd array big enough to store the image.  You have two errors - first, your variable is just one int, so when glReadPixels tries to write about a few hundred thousand bytes into that location it  writes far beyond the limits of what you've allocated, which, well, is a segmentation fault.  

Also declaring it as a local variable like that will kill it anyway.  You probably want something vaguely like 

```

GLuint *texture = (GLuint*) malloc (SCREEN_WIDTH * SCREEN_HEIGHT * 3);
    
    glReadPixels( 0, 0, SCREEN_WIDTH, SCREEN_HEIGHT, GL_RGB, GL_UNSIGNED_INT, texture );
    
    return texture;

```

---


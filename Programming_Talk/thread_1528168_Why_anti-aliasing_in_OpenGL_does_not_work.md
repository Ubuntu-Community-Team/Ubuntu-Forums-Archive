---
title: "Why anti-aliasing in OpenGL does not work?"
date: 2010-07-10
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2010-07-10
I want to get anti-aliased polygons in my OpenGL app.

First, I tried forcing both FSAA and adaptive anti-aliasing ON in amdcccle, but nothing happened.

Then I tried this:
```
SDL_GL_SetAttribute( SDL_GL_MULTISAMPLEBUFFERS, 1 );
SDL_GL_SetAttribute( SDL_GL_MULTISAMPLESAMPLES, 4 );
glEnable( GL_MULTISAMPLE );
```

It didn't work, so I tried this:
```
glEnable( GL_LINE_SMOOTH );
glEnable( GL_POINT_SMOOTH );
glEnable( GL_POLYGON_SMOOTH );
glHint( GL_LINE_SMOOTH_HINT, GL_NICEST );
glHint( GL_POINT_SMOOTH_HINT, GL_NICEST );
glHint( GL_POLYGON_SMOOTH_HINT, GL_NICEST );
```

Didn't work either so I tried doing FSAA manually with FBO's.

I got a segfault when the program called glGenBuffers(). glewinfo tells me I got GL_EXT_framebuffer_object. 
And my program is already using VBO's so glew is properly initialized. Why it doesn't work?

---


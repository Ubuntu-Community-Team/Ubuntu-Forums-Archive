---
title: "[SOLVED] Anyone know a fair deal about glClear()?"
date: 2008-08-03
forum: Programming Talk
---

### Post by Zeotronic on 2008-08-03
C++/OpenGL: My specific question is about how glClear works... I know there are the four buffers it can clear, but I don't entirely understand how that works... GL_COLOR_BUFFER_BIT seems pretty straight forward to me (though if it's not truely so obvious, please inform me), but if I declare glClear(GL_DEPTH_BUFFER_BIT), for example (and most specifically) what will that do? Does that ignore the depth of all the previous things I rendered, thus allowing me to essentially draw things behind the previously rendered things, through them in a seemingly glitchy manner that I am realizing I may not clearly be explaining? (and made more confusing by writing my realization of such?) I figure I need to know because I might be able to make use of that. **So if someone could tell me what glClear(GL_DEPTH_BUFFER_BIT) does, and how to render things regardless of their depth? (though I still want depth testing on... yea, this is a HUD thing)**

---

### Post by hod139 on 2008-08-03
Have you read the man page description?
  [http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/clear.html](http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/clear.html)

glClear will clear the specified buffer (specified by the bitwise mask passed to the function) to the specified clear color.  Therefore,  glClear(GL_DEPTH_BUFFER_BIT) will clear the depth buffer.  The depth buffer (also called the z-buffer) stores depth information about each pixel in the framebuffer.  For more details on the frame buffer and the various buffers it contains, I suggest you look at the openGL red book.  An older version of the red book is available online for free, and chapter 10 explains the framebuffer and the z-buffer:

[http://glprogramming.com/red/index.html](http://glprogramming.com/red/index.html)

---


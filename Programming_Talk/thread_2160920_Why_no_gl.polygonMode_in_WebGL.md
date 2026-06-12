---
title: "Why no gl.polygonMode in WebGL?"
date: 2013-07-08
forum: Programming Talk
---

### Post by bird1500 on 2013-07-08
Hi,
wireframe mode [[glPolygonMode]("http://www.opengl.org/sdk/docs/man3/xhtml/glPolygonMode.xml")(GL_FRONT_AND_BACK, GL_LINE)] is useful and stays part of the OpenGL core profile, yet in WebGL it's been removed, any ideas why or how one can work around?

Point in case, I need to make a scene (cube) as on the attached image, you'd draw a "filled cube", change polygon mode to GL_LINE and draw a "wired" cube on top of it with the same shader and buffer if gl.polygonMode was available, but since it's not I have to create 2  buffers, one for a filled cube and one for a cube of lines.

---


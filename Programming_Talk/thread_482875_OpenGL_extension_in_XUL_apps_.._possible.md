---
title: "OpenGL extension in XUL apps .. possible?"
date: 2007-06-24
forum: Programming Talk
---

### Post by moshy on 2007-06-24
Does anyone know an easy and simple way to do this if the OpenGL stuff is all done in native XPCOM components,
so that all you had to do was call some sort of equivalent of SDL_GL_SwapBuffers(); and it would get rendered into XUL.

---

### Post by luopio on 2007-11-06
Any updates on this? I'm very interested in bringing OpenGL into my XUL project as well (want to do compositing, transparent eyecandy, etc.).

So far I've found sources stating that the only way is to embed a native screen utilizing OpenGL and build a XPCOM interface for it.


Sources so far:
[http://groups.google.com/group/mozilla.dev.tech.xul/browse_thread/thread/9b7ef622bbd0283a](http://groups.google.com/group/mozilla.dev.tech.xul/browse_thread/thread/9b7ef622bbd0283a)
[http://libufo.sourceforge.net/index.html](http://libufo.sourceforge.net/index.html)

---

### Post by moshy on 2007-11-06
No, no updates for me. I had the same first source as you, but had no idea how to get it to work. You can do it in a java applet, then load the web page in xul if you want though.

---


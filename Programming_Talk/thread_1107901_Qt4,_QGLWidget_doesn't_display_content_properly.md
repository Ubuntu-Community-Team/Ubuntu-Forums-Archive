---
title: "Qt4, QGLWidget doesn't display content properly"
date: 2009-03-27
forum: Programming Talk
---

### Post by oujgazoiro on 2009-03-27
Hi,

I was trying to learn OpenGL and was using Qt4 for it. So I created an QGLWidget and inserted the code I found in a tutorial ([http://nehe.gamedev.net/]("http://nehe.gamedev.net/")). The code compiles and I can run the application but it shows a strange behavior:
It doesn't display the OpenGL content (which is a white triangle and a white rectangle on a black background). Instead it shows some disturbed image containing colors from my menubars, for example...
The point is, it does show the content if I resize the window, sometimes also if I move the window. 

I encountered the same problem with my installation of SciLab, when I plotted a function an empty window appeared. But after resizing, it displayed my plot, so I do think it could be a problem with my Ubuntu or GNOME or whatever.

Any ideas?

Thank you!

---

### Post by maddog39 on 2009-03-27
This sounds like strange behavior and I cant really put my finger on whats going on. But it sounds like the content isnt being rendered right away, instead its only being rendered when a resize event is issued. Though that doesn't answer the other question of, why is SciLab having a similar side effect. I'm not sure to be honest but just some thoughts.

---


---
title: "OpenGL glEnable (GL_LIGHTING) and glColor3f do not work together."
date: 2009-06-28
forum: Programming Talk
---

### Post by thomas9459 on 2009-06-28
Hello. I have been writing c++ programs that use OpenGL for quite a while now and know a lot of OpenGL's features. But recently I have hit a ](*,) in my program. I downloaded the [Linux/SDL conversion]("http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=13") of NeHe 13th tutorial and am currently trying to merge it with another one of my programs but when I added glEnable(GL_LIGHTING) all color just went white. Did anybode else have this problem. How did you fix it. Please help.
Here are the 2 screenshots.
[ATTACH]119262[/ATTACH][ATTACH]119263[/ATTACH]

---

### Post by thomas9459 on 2009-06-28
Found my answer at [Basic OpenGL Lighting]("http://www.sjbaker.org/steve/omniv/opengl_lighting.html"). If you enable lighting you need to use ```
glColorMaterial ( GL_FRONT_AND_BACK, GL_AMBIENT_AND_DIFFUSE )
glEnable ( GL_COLOR_MATERIAL )
``` functions for glColor to do anything. Once you use the functions, glColor will do what it does best. ;)

---

### Post by sickanimations on 2011-04-27
Thanks, this was exactly what I was looking for. Funny that the OpenGL Programming Guide (red book) doesn't mention this.

---


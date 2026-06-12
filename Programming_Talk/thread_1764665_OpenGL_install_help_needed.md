---
title: "OpenGL install help needed"
date: 2011-05-22
forum: Programming Talk
---

### Post by jimpbr on 2011-05-22
Hi,

I want to start writing opengl apps in C++ on Ubuntu. I have installed the following packages:
freeglut3
freeglut3-dev
libglew1.5
libglew1.5-dev
libglu1-mesa
libglu1-mesa-dev
libgl1-mesa-glx
libgl1-mesa-dev

I write some test program and have the include statement for example:
#include < GL/glut.h >

I get the error:
GL/glut.h : No such file or directory
I checked and all the headers are stored in 'usr/include/GL'. But still the compiler isn't detecting them.
So what am I missing?

Cheers,
Jim

---

### Post by PaulM1985 on 2011-05-22
When I set mine up I followed this tutorial.  [http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup_linux/video.php](http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup_linux/video.php).  I have found that these tutorials have been very helpful and I would recommend watching Part 0 (setting up) and part 1 (the basics) if you are looking to learn opengl.  Here is a link to the main page: [http://www.videotutorialsrock.com/](http://www.videotutorialsrock.com/)

Paul

---

### Post by jespdj on 2011-05-22
That header file should have been installed with the package freeglut3-dev. Have you checked if the file exists: /usr/include/GL/glut.h

> **jimpbr said:**
> I write some test program and have the include statement for example:
#include < GL/glut.h >

Are you typing it literally like that? Remove the spaces in between the < and >. So:

```
#include <GL/glut.h>
```
Not:
```
#include < GL/glut.h >
```

---

### Post by jimpbr on 2011-05-23
Ha!
That got it! 
Yeah I saw it written on some other forum post as < GL/glut.h > ie with the spaces and naively copy/pasted it^^.
Thank heavens it was something trivial! I thought I was losing it for a minute.
Cheers,
Jim

---


---
title: "GL/glut library files not found?"
date: 2009-02-26
forum: Programming Talk
---

### Post by abhilashm86 on 2009-02-26
i'm trying OPENGL to do some basic geometry models, but when i tried and compiled, the GL/glut library functions were not there, how to include these ones, where will i get the library headers?please help

---

### Post by stumbleUpon on 2009-02-26
You have to install the development packages of the glut libraries

```
sudo apt-get install freeglut3-dev libglut3-dev
```

and then link against the libraries

```
-lm -lGL -L/usr/X11R6/lib -lGLU -lglut
```

to get an executable.

---

### Post by abhilashm86 on 2009-02-26
> **stumbleUpon said:**
> You have to install the development packages of the glut libraries

```
sudo apt-get install freeglut3-dev libglut3-dev
```

and then link against the libraries

```
-lm -lGL -L/usr/X11R6/lib -lGLU -lglut
```

to get an executable.

thanks a lot for the info, it just included libraries:)

---


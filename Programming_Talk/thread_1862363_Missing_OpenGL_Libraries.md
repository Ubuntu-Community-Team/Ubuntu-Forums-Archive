---
title: "Missing OpenGL Libraries"
date: 2011-10-16
forum: Programming Talk
---

### Post by pheserus on 2011-10-16
I recently installed Xubuntu 11.10, and as I tried to recompile one of my C++/OpenGL applications that I got a bunch of errors.

I used this command:
> g++ -lSDL -lGL -lGLU main.cppAnd I got:
> undefined reference to `glBegin'
undefined reference to `glVertex3f'
undefined reference to `glEnd'Those are just a few. the list is really long. I was able to compile just fine before, so I checked and I can't find any of the OpenGL libraries that I used to have. Can anyone tell me what packages I need to install?

---

### Post by MadCow108 on 2011-10-16
libraries need to be behind objects needing their symbols:
```
g++ main.cpp -lSDL -lGL -lGLU 
```

this is due to the linker flag --as-needed which is now default in ubuntu 11.10

---

### Post by pheserus on 2011-10-16
Ah thanks! I never would have guessed that was that problem. xD
TY So much!

---


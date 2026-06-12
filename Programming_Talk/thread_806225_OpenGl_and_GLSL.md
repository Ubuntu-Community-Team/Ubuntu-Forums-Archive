---
title: "OpenGl and GLSL"
date: 2008-05-24
forum: Programming Talk
---

### Post by gorded on 2008-05-24
Hey I just started using opengl on linux and decide to delve into GLSL, but when i compile my program that links my shaders to a program object. i get 

g++ -c -g -I/usr/include/ -I./ rasta.cpp
rasta.cpp: In function ‘void Init(int, char**)’:
rasta.cpp:43: error: ‘glCreateProgram’ was not declared in this scope
rasta.cpp:44: error: ‘glCreateShader’ was not declared in this scope
rasta.cpp:47: warning: deprecated conversion from string constant to ‘char*’
rasta.cpp:48: warning: deprecated conversion from string constant to ‘char*’
rasta.cpp:50: error: ‘glShaderSource’ was not declared in this scope
rasta.cpp:53: error: ‘glCompileShader’ was not declared in this scope
rasta.cpp:56: error: ‘glAttachShader’ was not declared in this scope
rasta.cpp:59: error: ‘glLinkProgram’ was not declared in this scope
rasta.cpp:60: error: ‘glUseProgram’ was not declared in this scope

i include : Gl/gl.h  Gl/glu.h Gl/glut.h Gl/glext.h

glext.h has the forward declaration for all of the function i use. But i dont think its being included. I think its a problem with my makefile, since i am horrible at making them(no pun intended).

Here is my Makefile and Make.config any help is greatly appreciated thanks :D

```
include Make.config

OBJS = rasta.o
TARGET = rasta

all: rasta

rasta: rasta.cpp
	$(CC) $(CFLAGS) rasta.cpp
	$(CC) $(CFLAGS) $(OBJS) $(LFLAGS) -o $(TARGET)

```

```

CC = g++
CFLAGS = -c -g -I/usr/include/ -I./
LFLAGS = -lGL -lglut -lm
```

---

### Post by destructchaos on 2008-05-24
I haven't used GLSL before, but it sounds like you need to add it to your LFLAGS.

The two warning can be fixed by making the (char *) const.

---

### Post by geirha on 2008-05-24
In glext.h, glCreateProgram is declared inside an "#ifdef GL_GLEXT_PROTOTYPES", so adding -DGL_GLEXT_PROTOTYPES to the CFLAGS should make it compile. Haven't greped for the other missing declarations, but chances are they'll disappear too.

---


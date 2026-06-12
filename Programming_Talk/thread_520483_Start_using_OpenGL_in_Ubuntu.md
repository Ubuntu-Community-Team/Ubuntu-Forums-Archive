---
title: "Start using OpenGL in Ubuntu"
date: 2007-08-08
forum: Programming Talk
---

### Post by whodoo on 2007-08-08
I want to start to develop OpenGL applications in Ubuntu. How can I do this? (Im fairly experienced with OpenGL in Windows, so Im just asking how to setup OpenGL in Ubuntu). First, I need to download and install the libraries with the headers and all that, where can I do that? Secondly, should I "wrap" my program using another graphics library to make it easy to create windows and that stuff? And, the last question is pretty embarrasing, but Im used to Visual C++, how do I compile my programs, linking the right libraries?

Im pretty unfamiliar to Linux so it would be great if I didn't have to compile anything on my own or anything.

---

### Post by bbzbryce on 2007-08-08
> **whodoo said:**
> I want to start to develop OpenGL applications in Ubuntu. How can I do this? (Im fairly experienced with OpenGL in Windows, so Im just asking how to setup OpenGL in Ubuntu). First, I need to download and install the libraries with the headers and all that, where can I do that? Secondly, should I "wrap" my program using another graphics library to make it easy to create windows and that stuff? And, the last question is pretty embarrasing, but Im used to Visual C++, how do I compile my programs, linking the right libraries?

Im pretty unfamiliar to Linux so it would be great if I didn't have to compile anything on my own or anything.

Install the glut and glew libraries via aptitude. After that just make sure you include their headers. Glut is a openGL utility toolkit which helps making windows and glew is for openGL extensions.

#include <GL/glew.h>
#include <GL/glut.h>

Then compile by doing:
g++ something.cpp -lglut -lGLEW

---

### Post by Wybiral on 2007-08-08
My vote would be on using SDL to initialize the window and handle events.

It's portable, commonly used, and it has some really good helper libraries (SDL_ttf for rendering text, SDL_mixer for audio, SDL_image for loading textures...)

NeHe has an SDL version for most of their tutorials (with Makefiles too).

---

### Post by slavik on 2007-08-09
not to brag, but find my code, it uses SDL and OpenGL :)

---

### Post by vexorian on 2007-08-09
SDL == +

You'll be able to release a windows version of your game.

windows version = more users.

more users = more Linux users.

more cross platform software == let's show some companies how inept their developers are for focusing on a single platform.

Oh, and when I released the source distro of my SDL game, people began porting it to platforms I would never think of supporting (since I didn't install them)

If you do it correctly it might even get ported to OS/X

---


---
title: "I want to make a cross-platform game, witch language&amp;lib should I use?"
date: 2011-06-13
forum: Programming Talk
---

### Post by wing129983 on 2011-06-13
I can make the game by dx. But I just removed windows from my computer and installed ubuntu.....so I want it can be play under win&ubuntu. 
I just want to make a 2D game, but I need alpha blend. And it's an action game(use joystick maybe). So, witch way is better? C/C++&sdl, or lwjgl(light weight java game library), or I should use C/C++&opengl&openal directly? ( easy, fast, stable;))

Please forgive my poor English. Many thanks.

---

### Post by worseisworser on 2011-06-13
Java.

---

### Post by juancarlospaco on 2011-06-13
Python

---

### Post by NovaAesa on 2011-06-13
I would go for SDL (with the addition of open gl if you need it) and the language of your choice.

---

### Post by simeon87 on 2011-06-13
Assembly.

---

### Post by geirha on 2011-06-13
Making a C/C++ program that'll work on both Windows and Unix-like systems takes a bit of experience. You should definitely have a Windows system available for test building.

With java you don't have to worry about that. If it works on your Ubuntu system, it is very likely to also work on Windows (as long as all the libraries you use are installed of course).

Python programs will generally also work fine on all platforms, but there are pitfalls that'll make it fail on other systems. You should have a Windows system available for testing.

---

### Post by Petrolea on 2011-06-13
For a great compatibility you would use Java + libraries that you can port to Windows. You could also use Swing to make it even more portable but that's not really meant for games (and even if you would make a game with Swing it would probably have VERY HIGH RAM usage).

So, Java + lwjgl would work. 

There are many options, you could also use SDL which is portable to some point and is great for making games (but just SDL can't make a very good game itself). Check out Linux Game Programming (Google, first result, pdf, too lazy to copy-paste the link).

---

### Post by LoneWolfJack on 2011-06-13
> With java you don't have to worry about that.

Ya. Write once, debug everywhere.

---

### Post by PaulM1985 on 2011-06-13
> **Petrolea said:**
> So, Java + lwjgl would work. 

+1

This is what I am using at the moment.

Paul

---

### Post by wing129983 on 2011-06-13
Thanks to everyone. 

Assembly...?What a great work....

I can test my game by vm windows or using my friends' computer, so that's not an issue.

Java+lwjgl looks good, I will try it. And I will check linux game programming out.

Many thanks.

---

### Post by stchman on 2011-06-13
From what I have read, as long as you make your program use the openGL it will run run on any platform that has an openGL ICD.  The other forum game gurus can correct me if I'm wrong.

---

### Post by DangerOnTheRanger on 2011-06-14
Yes, you're right, *but* (and this is huge) OpenGL is only *an API.* The OP wants to know what language he should use.

My personal choice is Python. Python's main advantage (aside from being nicer on the eyes than C, C++ or even Java [I can prove this]) is that it's interpreted, instead of being compiled. This means you can develop your game on Linux, and with little to no modifications, get it to work on Windows and Mac OSX. I myself develop a Python game engine that is known to work on Windows 7 and Linux, and I don't own a Windows 7 machine!

A common misconception you'll see in many places (including here) is that Python is too slow for game development. People who state that assume that you are making a 3D game *and* you will be directly making calls to the OpenGL library, which isn't normally the case (most Python game engines are written in C++).

There are also plenty of good 2D game libraries for Python:

[LIST]
[*]Pygame ([http://pygame.org]("http://pygame.org/")) - a Python wrapper around SDL
[*]Pyglet ([http://pyglet.org]("http://pyglet.org/")) - A pure-Python (i.e, it's written completely in Python) game library with support for fast hardware-accelerated rendering. One nice advantage of Pyglet is that since it's pure-Python, you can bundle it with your game, without worrying what OS your users are using
[*]PyOpenGL ([http://pyopengl.sf.net]("http://pyopengl.sf.net/")) - A pure-Python wrapper around OpenGL
[*]Rabbyt ([http://arcticpaint.com/projects/rabbyt/](http://arcticpaint.com/projects/rabbyt/))  - A nice 2D sprite library for Python
[/LIST]
Hope this helps!

---

### Post by Petrolea on 2011-06-14
> **stchman said:**
> From what I have read, as long as you make your program use the openGL it will run run on any platform that has an openGL ICD.  The other forum game gurus can correct me if I'm wrong.

You can't make a game only with OpenGL, you must use some other tools too. OpenGL might be portable, but those tools probably won't be (at least not 100%). For example: SDL + OpenGL.

---


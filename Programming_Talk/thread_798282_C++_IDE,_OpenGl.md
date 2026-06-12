---
title: "C++ IDE, OpenGl"
date: 2008-05-18
forum: Programming Talk
---

### Post by ngates87 on 2008-05-18
can any help me in setting up a decent ide some im can do some OpenGl programming, I've used Glut, and have no problem switching to freeglut or SDL, but I'm lost as how to link include files, and libary files, i have tried getting it to work in Netbeans, and ive tried compiling projects i know that work, and still have problems, with functions calls, even after including the glut.h header file.

---

### Post by ngates87 on 2008-05-18
> **ngates87 said:**
> can any help me in setting up a decent ide some im can do some OpenGl programming, I've used Glut, and have no problem switching to freeglut or SDL, but I'm lost as how to link include files, and libary files, i have tried getting it to work in Netbeans, and ive tried compiling projects i know that work, and still have problems, with functions calls, even after including the glut.h header file. I have to say this is so easy to do in Visual Studio, such as linking lib and header files, so i would greatly appericate any help with this pu pu please?

---

### Post by slackerwarenative on 2008-05-18
ngates87, you have a couple of options, which depend of preference, experience and targeted platform.

When programming C++ on linux, I usually just use gedit and g++. Alternatively you could use
 [Anjuta]("http://anjuta.sourceforge.net/"), 
[KDevelop]("http://www.kdevelop.org/") or 
[Eclipse]("http://www.eclipse.org/") (mostly Java, but can handle C++ when setup to do so), all great IDEs which tie into gcc/g++.

When I am on linux and want/need to compile (non-release) for a Win32 based system, I use Dev-C++ under wine. It runs great, installs great and compiles great. The package manager even can grab the devpaks online and install them. If you are a beginner and are using a fast machine or want to port between win32, dos and GNU C Compiler compatibles (Linux, Unix, BeOS,etc.), I would recommend this option. Note that whatever you compile with it must be run with wine. Despite this, you can just use the IDE, which will make porting easier. If you install the devpaks, it will setup the libs and templates for you.

[Dev-C++]("http://www.bloodshed.net/dev/devcpp.html")

If you go the gcc / g++ route, you can link libraries by adding "-l". You could type something like this, you can probably drop some of these to make your binary smaller. You WILL need "-lglut" and "-lGL":

```
gcc your_file.c -o your_compiled_file -L/usr/X11R6/lib -lglut -lGL -lGLU -I/usr/X11R6/include -lX11 -lXext -lXmu -lXi
```

Good luck, and I hope that helps.

---

### Post by moma on 2008-05-18
Hello,

Take a look at this guide. It will show you how to set up the Code::Blocks IDE.
[http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)

Read the notes [COLOR="Red"][Note 1][/COLOR] to [COLOR="Red"][Note 5][/COLOR] very carefully. 
[COLOR="Red"][ Note 7 ][/COLOR] will tell you about SDL applications.

---

### Post by Jem Masters on 2009-05-31
I need help setting up OpenGL with Anjuta.  I add the "GL" and "GLUT" libraries under "libraries" but when I execute any example code nothing show up and the worst thing is that no error appear at the debugger. Any help?

---


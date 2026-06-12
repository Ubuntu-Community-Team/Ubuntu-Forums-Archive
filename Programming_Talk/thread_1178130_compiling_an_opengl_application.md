---
title: "compiling an opengl application"
date: 2009-06-04
forum: Programming Talk
---

### Post by garg89 on 2009-06-04
i have a code in opengl that use glut and glui library of opengl for rotating and moving large data sets. i am unable to run the code on my machine as both these lib. are missing from my system and i am unable to download them. 
can anyone tell me how can i modify my code so that it will work without these libraries.

---

### Post by Volt9000 on 2009-06-04
Well, you can't. If the program was written with those libraries, the only way to run it without them is to comment out all references to functions from those libraries. But of course that means the program won't work as expected.

Why can't you download the files?

---

### Post by abhilashm86 on 2009-06-05
install basic libraries for opengl, open terminal and type
```

sudo apt-get install freeglut3-dev libglut3-dev

```

then compile with .cpp filename with linking following,

CODE]
g++ pgmname.cpp  -lm -lGL -L/usr/X11R6/lib -lGLU -lglut

-lm -lGL -L/usr/X11R6/lib -lGLU -lglut
[/CODE]

if you want to create an IDE for opengl,
[http://ubuntuforums.org/showthread.php?t=590676](http://ubuntuforums.org/showthread.php?t=590676)

[http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)

---


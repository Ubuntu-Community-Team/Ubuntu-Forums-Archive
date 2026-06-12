---
title: "glut newbie"
date: 2005-09-20
forum: Programming Talk
---

### Post by andy.perko on 2005-09-20
G'day!

First of all, a big thank-you to the Ubuntu team!  Have been using it since Hoary, and I must say, I'm never going back to Windows!

On to the problem:
I am just starting an OpenGL course where we use GLUT.  We were given a sample program to basically copy/paste and compile.  I can get it to compile by changing the first two lines as follows:

```

// #include <glut.h>
#include <GL/freeglut.h>


``` 

BUT, although it compiles (using Anjuta), it won't build!  Every reference to any GLUT command gives me a similar error:

undefined reference to `glClearColor'
.... etc etc for all gl references

I'm using Breezy Preview, Anjuta and have build-essential installed.  Also tried this when I was using Hoary with no success.

Thanks in advance

---

### Post by andy.perko on 2005-09-20
Nevermind!  I should have checked the error message in Google first!

found out I had to use -lglut in the compile command.

---


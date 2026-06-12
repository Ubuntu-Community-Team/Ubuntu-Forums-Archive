---
title: "glut?"
date: 2006-01-23
forum: Programming Talk
---

### Post by bartbes on 2006-01-23
I want to program (with c++) in openGL, but I need glut... does anyone knows how to get glut, I've downloaden glutg3 and I already had glut3 and libglut3 why do I still get this error:
1.cpp:3:21: fout: GL/glut.h: Onbekend bestand of map

---

### Post by Viro on 2006-01-23
You need to install the package libglut3-dev to get the headers and necessary library files.

---

### Post by aeuo on 2009-09-12
Hello!

ubuntu has 
freeglut3 - OpenGL Utility Toolkit
glutg3 - the OpenGL Utility Toolkit
libglut3 - the OpenGL Utility Toolkit

what is the difference between them?

---

### Post by 0xABC123 on 2009-11-25
Remove all other glut packages and install freeglut3 and freeglut3-dev.

Also, you should #include <GL/freeglut.h> instead of <GL/glut.h>, because <GL/glut.h> doesn't have some function prototypes such as glutMouseWheelFunc().

---

### Post by jespdj on 2009-11-25
Guys, do you realize you're answering a question that was asked in February 2006? The OP is probably not still waiting for an answer...

---

### Post by dage on 2009-11-26
thank you, I still find your answer userful for me

---

### Post by ghostcoil on 2010-01-23
I also found this post helpful, as old as it is : )

---

### Post by rachka on 2010-02-06
> **dage said:**
> thank you, i still find your answer userful for me

+1

---

### Post by Bruce! on 2010-02-06
Yes, still helpful. Thanks.

---

### Post by CrammitTheFrog on 2010-02-21
I also found it helpful.

---

### Post by zendari on 2010-06-09
I register new account from 2400 public 
terminal in center market and risk 
persecution from luddites to make post
saying how helpful this is to me. THank
you my friends.

---

### Post by steele64e on 2010-08-11
still a great thread, it's the first result on google [glut ubuntu]

---

### Post by RandomLinuxUser on 2010-10-19
This was very helpful to me thank you!

---

### Post by weeix on 2011-01-24
thanks a lot :p

---

### Post by Simian Man on 2011-01-24
Glut is OK for simple things, but way too restrictive for anything else.  SDL and GLFW do the same things glut does much better.

---


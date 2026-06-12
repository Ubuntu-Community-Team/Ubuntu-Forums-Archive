---
title: "OpenGL using Ubuntu"
date: 2008-04-14
forum: Programming Talk
---

### Post by Cesar Ghali on 2008-04-14
Dear friends...

I am new to Ubuntu Linux. I want to write programs using OpenGL Library, but I don't know the name of the package or packages that I need to install using Synaptic.

Please can anyone please help me.

Another thing is that I can compile the OpenGL program using gcc command or not...


Please I need you help because I have been trying this for three weeks.


Thanks

---

### Post by Lster on 2008-04-14
Hi! I had the same question, too, when I came to Ubuntu. I believe the following thread sorted everything out, for me:

[http://ubuntuforums.org/showthread.php?p=2365634#post2365634](http://ubuntuforums.org/showthread.php?p=2365634#post2365634)

Hope it helps,
Lster

---

### Post by Cesar Ghali on 2008-04-15
Dear friends...

Thanks a lot Lste, your thread gave me a lot of help, but I was wondering about doing the following:

In Microsoft Windows, I use code in the attached file to create a window then draw a polygon inside it. The thing is that I want to use the same code in Ubuntu. The problem is that after I installed some packages that contain OpenGL header files, I located the file glut.h and open it and found the prototypes of the functions glutInitWindowPosition, glutInitWindowSize, etc..., but without the bodies (I don't know if this is normal), but I still got error while I am trying to compile the code using gcc, any ideas???.

Thanks in advance for your help...

---

### Post by heikaman on 2008-04-15
> **Cesar Ghali said:**
>  I located the file glut.h and open it and found the prototypes of the functions glutInitWindowPosition, glutInitWindowSize, etc..., but without the bodies (I don't know if this is normal)


yeah It's normal, It's called a header file ! and the implementation is in a static/shared library.

> **Cesar Ghali said:**
> 
 but I still got error while I am trying to compile the code using gcc, any ideas???


Yes if we are psychics  :) but I'm guessing you didn't link the glut lib.
append to the compilation command:

-lglut

---

### Post by Cesar Ghali on 2008-04-15
Thanks heikaman for your reply, but I don't know how to link the glut lib, can you please tell me how to do it? becuase I am very new to Ubuntu.

Thanks in advance for your help...

---

### Post by heikaman on 2008-04-15
It's not about Ubuntu or Windows, It's about C/C++ programming :), I really think you should read a good C++ programming book first before jumping into opengl.

Then read this excellent introduction to glut:

[http://mindfuck.de-brauwer.be/articles/glut/]("http://mindfuck.de-brauwer.be/articles/glut/")


and I told you how to link glut, but again :

```

g++ prog_name.cpp -o prog_name -lglut

```

---

### Post by Cesar Ghali on 2008-04-15
Thanks heikaman, and sorry for asking a lot.

I am a C# programmer since 2004, but I am new to OpenGL in C/C++ and very very new to Ubuntu because I have begin using it for only 2 weeks.

Thanks again, your last command is perfectly working.

---

### Post by mikesofty on 2008-04-21
Is it possible to make buttons in opengl or glut

---

### Post by Wybiral on 2008-04-21
GLUT has some crude menu functionality built in, not sure if it's worth much though...

There are GUI libraries for OpenGL that have those sorts of things implemented already, you might try googling around for some.

You can also write buttons on your own using "collision" with the mouse and a quad or something for the button. It's not too hard, just render a quad, check if the mouse is in it when a click happens, and callback something from there.

---


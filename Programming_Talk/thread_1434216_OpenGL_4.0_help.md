---
title: "OpenGL 4.0 help"
date: 2010-03-20
forum: Programming Talk
---

### Post by CreativeOne on 2010-03-20
Hello, I am new to opengl, and have two questions about the new version of OpenGL, 4.0. 

     1.How would I get the full graphical power of OpenGL 4.0 in a open source game engine like crystal space. would I use the glut, or what. otherwise what I'm saying is how would I incorporate this into the engine.

     2.Does OpenGL 4.0 come with the latest version of ubuntu already (9.10 or 10.04), and if not, how do I install it.

Your answers are greatly appreciated, thanks.

---

### Post by gusnan on 2010-03-20
The first thing you need is drivers for your graphics card to support openGL 4 - Nvidia is currently working on 3.3 - so I doubt you'll see GL 4 support very soon there - see 

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

Don't know about intel or ATI/AMD though.

---

### Post by ApEkV2 on 2010-03-20
> **CreativeOne said:**
> Hello, I am new to opengl, and have two questions about the new version of OpenGL, 4.0. 

     1.How would I get the full graphical power of OpenGL 4.0 in a open source game engine like crystal space. would I use the glut, or what. otherwise what I'm saying is how would I incorporate this into the engine.

     2.Does OpenGL 4.0 come with the latest version of ubuntu already (9.10 or 10.04), and if not, how do I install it.

Your answers are greatly appreciated, thanks.

OpenGL 4.0 isn't on any new mainstream graphics cards yet, so your prog would be for a select few.
You should use SDL instead of glut. glut's mainly for testing purposes.

---

### Post by Sockerdrickan on 2010-03-20
> **CreativeOne said:**
> Hello, I am new to opengl, and have two questions about the new version of OpenGL, 4.0. 

     1.How would I get the full graphical power of OpenGL 4.0 in a open source game engine like crystal space. would I use the glut, or what. otherwise what I'm saying is how would I incorporate this into the engine.

     2.Does OpenGL 4.0 come with the latest version of ubuntu already (9.10 or 10.04), and if not, how do I install it.

Your answers are greatly appreciated, thanks.
OpenGL is not something that you just "plug in". You need excessive  programming skills. And why do you need 4.0 anyways, do you even know what it has got to offer that 3.3 hasn't got?

---

### Post by CreativeOne on 2010-03-20
Well, doesn't opengl 4.0 have tessellation support, but 3.3 doesn't?
Thanks for the responses.

---

### Post by Sockerdrickan on 2010-03-20
I am just saying that if you are "new to OpenGL" you might have to cover some basics first. Google for some 3.2 tutorials

---

### Post by Deluxe224 on 2010-03-20
I need help1

---

### Post by anders_c_ on 2010-03-25
Good news! AMD has released preview drivers with OpenGL 4.0 support for their HD 5XXX series:D
[http://www.phoronix.com/scan.php?page=news_item&px=ODEwMQ]("http://www.phoronix.com/scan.php?page=news_item&px=ODEwMQ")

---

### Post by dumbsnake on 2010-03-27
I was at GDC where they announced OpenGL 4.  I even went to the party that Khronos threw.  Anyway, while I was at GDC I asked folks from both NVidia and ATI.  They both basically said that any Direct3D 11 card should have OpenGL 4 support because the hardware already supported it.  All that is to say, it isn't far off and you'll have the improvements of OpenGL 4 soon assuming your card supports it.  Whether you know how to make use of OpenGL 4 is clearly a separate question.  Happy coding everyone.

---


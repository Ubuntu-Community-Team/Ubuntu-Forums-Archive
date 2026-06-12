---
title: "graphics program problem"
date: 2009-02-26
forum: Programming Talk
---

### Post by abhilashm86 on 2009-02-26
i am doin graphics programming using OPENGL, when i compile and execute programs, following errors occur, i'm quite puzzled why performance hurts and what is meaning of it?


abhilash@abhi:~$ g++ open1.cpp -lm -lGL -L/usr/X11R6/lib -lGLU -lglut
abhilash@abhi:~$ ./a.out
freeglut (./a.out): Unable to create direct context rendering for window 'circle'
This may hurt performance.


so how to create rendering, if u need program code,i can post it

---

### Post by abhilashm86 on 2009-02-26
any help or any ideas u know, i don't know why this warning, i googled but din't find the answer

---

### Post by jespdj on 2009-02-26
What graphics card do you have in your computer and what graphics driver are you using? This error message sounds like you are not using a graphics driver that provides hardware-accelerateed 3D graphics support.

---

### Post by abhilashm86 on 2009-02-26
> **jespdj said:**
> What graphics card do you have in your computer and what graphics driver are you using? This error message sounds like you are not using a graphics driver that provides hardware-accelerateed 3D graphics support.

oh is that the problem, ok,i use nvidia 128MB graphics card which is inbuilt with motherboard, i din't install anything in ubuntu.......
like we install driver cd in windows,how to overcome this error

---

### Post by hessiess on 2009-02-26
Install the propiatery driver from the restricted driver manager.

---


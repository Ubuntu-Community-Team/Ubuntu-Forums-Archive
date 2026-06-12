---
title: "which language is best for webcam image processing"
date: 2009-11-21
forum: Programming Talk
---

### Post by jakjoseph on 2009-11-21
Hi i'm new to ubuntu programming. i'm intending to develop a software which can access webcam and process the images coming from it for applications like face recognition color tracking etc. i dont know which language i should start with. please help me to select a programming language for this application. i'm good at c and c++. 
thanks in advance

---

### Post by tatrefthekiller on 2009-11-21
For image processing, you need a fast language, if you know C/C++, I think it's fine. You just have to find good libraries to access webcam.

---

### Post by moe_syzlak on 2009-11-21
Don't forget c#, or even java (depending on the platform and resources avail.)

---

### Post by jakjoseph on 2009-11-21
i installed opencv in ubuntu.
i want to compile and run .cpp example files that came with it.
please help.

---

### Post by grayrainbow on 2009-11-21
First: there's no such thing as Ubuntu programming! It's Linux programming!

About the image manipulations, it really depends what you want, and what library you are used to use. For simple prototype you can do with Mono(if there's wrappers to v4l), probably python got wrappers for that as well, and expect every additional binding to make real impact on algorithm you use couse webcams usually don't run with very high frame rates anyway. For everything more serious(as working application) you'll need C/C++(you can add OpenGL, after all graphics cards are exactly for image manipulations,but that if already really know C/C++). I personal find v4l with C++ ideal for my laptop cam when I want to play with it.

[http://www.linuxtv.org/wiki/index.php/Main_Page]("http://www.linuxtv.org/wiki/index.php/Main_Page")

---


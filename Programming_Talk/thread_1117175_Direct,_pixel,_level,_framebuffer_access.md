---
title: "Direct, pixel, level, framebuffer access"
date: 2009-04-05
forum: Programming Talk
---

### Post by JFASI on 2009-04-05
I have decided to put my linear algebra class experience to the test and write a small, educational, 3d graphics library. I was thinking if doing it in Java and using Processing.org, but the more I think about it, the more I realize that using Java for anything as intensive as 3d computation is a bad idea. 

My next choice was C++, but I can't think of any graphics libraries low level enough to allow me to draw pixels directly on the screen/window. In all fairness, the framebuffer is probably lower than I want to go, but I think you see what I mean. I'd want some support for mouse and keyboard input, too.

---

### Post by benj1 on 2009-04-05
have you had a look at sdl for c++?
[http://www.libsdl.org/index.php](http://www.libsdl.org/index.php)
i think quickcg is built on top of it so you might want to have a look at that too. 
[http://student.kuleuven.be/~m0216922/CG/index.html](http://student.kuleuven.be/~m0216922/CG/index.html)

---

### Post by JFASI on 2009-04-05
I like the looks of SDL. I was under the impression that it was a higher level thing, closer to OpenGL. It's nice and cross platform, to boot. 

Thanks for that one.

---

### Post by Npl on 2009-04-06
if you want to do software rendering, why dont you just render to a bitmap (ie an array of RGB-Values) and then paint that via gtk+, qt, SDL or whatever toolkit you want to use?
directly drawing pixels one-by-one is something you never should do (as it will be painfully slow), draw as much pixels as possible in one step.

---

### Post by cl333r on 2009-04-06
> ..and write a small, educational, 3d graphics library.
For such needs Java alone is more than enough and you can do well direct 2D rendering and build your 3D upon that and other interesting stuff.
Here's a hint to fast pixels drawing in Java:
[http://www.yov408.com/javagraphics/javagraphics.html](http://www.yov408.com/javagraphics/javagraphics.html)


Java also has bindings to openGL called JOGL, I bet you won't notice a difference compared to C++/OpenGL, especially since you're doing a "small, educational" project.

> the more I realize that using Java for anything as intensive as 3d computation is a bad idea
1) Java has evolved. C++ being like 300% faster no longer applies.
2) See the OpenGL binding above.

---

### Post by JFASI on 2009-04-06
While this is an educational project, I still plan on taking it to a very high level of sophistication, and I can see myself going into graphics after I graduate. As for right now, I have things proofed in Java, but I want to write them in C++, since it's an industry standard, and because, say what you like, it's faster. It also just happens to be really low level, which is how I like to do things. 

I like the ability to directly write to a buffer, then flipping it that I see SDL has, so I think I'll go with that. Thanks for the suggestions!

---


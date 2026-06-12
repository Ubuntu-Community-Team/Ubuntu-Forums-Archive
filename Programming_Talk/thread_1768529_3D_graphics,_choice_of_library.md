---
title: "3D graphics, choice of library"
date: 2011-05-26
forum: Programming Talk
---

### Post by vivichrist on 2011-05-26
hmm, I have looked at libcluttermm, libgtkglext various canvas libs and clanlib etc. what would be the best graphics library from an object oriented C++ or Java perspective? I want to make small games, graphics demo's in gtk and possibly portable java versions. I don't much like the procedural approach using C to program opengl apps.

---

### Post by PaulM1985 on 2011-05-27
Isn't rendering quite procedural anyway.  You have a series of polygons and call drawMyPolygon until they are all drawn.  You can have the creation of the polygons in object oriented code and then have a procedure to draw everything.

Just think about Java's paint(Graphics g) method on components.  All the stuff in that will be procedural to draw something.

For me, it has to be opengl.

Paul

---

### Post by Petrolea on 2011-05-27
Ever tried SDL or OpenGL? There are lots of tutorials on each of them (you might also want to use them together).

For Java there are lots of options. Swing can be used to draw shapes and stuff like that too + it comes with Java already.

---

### Post by t1497f35 on 2011-05-27
For a demanding cross-OS game you don't really have an option, just one word - OpenGL - which is usually used either through freeglut or through SDL.

Java's got no built-in 3D APIs and the 2D API isn't optimized for demanding games, in fact on Linux a lot (if not all) of Java's 2D API is done in software (no hw acceleration). The OpenGL rendering backend is disabled cause it's half backed and no one bothered updating it to make it work around bugs.
There's Java binding to OpenGL but I tried one sample a few months ago and it crashed I don't wanna look into Java's 3D solutions ever since.

And no, you don't have to use C or structural programming to program OpenGL, because your (C++) game is gonna be based on some type of engine anyway, cause no one is doing games from scratch.

As to clutter - I'm afraid it doesn't work on window$.

---

### Post by JupiterV2 on 2011-05-27
Wasn't Minecraft written in Java?

---

### Post by t1497f35 on 2011-05-27
There are games written in Java (i.e. using JOGL), even sophisticated ones, but they're very rare compared to the C++ ones, because Java while solving some issues introduces some of its own, which might be hard or impossible to fix, i.e. the Java VM seems stable and mature nowadays, but it still crashes from time to time, and when it does it takes down the game too, when I used Azureus it was taking down Azureus with it (now Azureus is called Vuze). Anyway, I'm myself a Java dev for quite some time and I learned that I'd only use Java for serious if it's about enterprise or mobile stuff.

---

### Post by Petrolea on 2011-05-28
> **JupiterV2 said:**
> Wasn't Minecraft written in Java?

Yes it was. But the RAM consumption is enormous.

---

### Post by vivichrist on 2011-05-29
hmmm I guess opengl is the way but if java opengl can't be hardware accelerated then I guess C++ is the only way. I was looking at lwjgl as a java 3d solution, looks good, documentation and all. and as I say "simple 3D graphics" stuff that I can do as a solitary programmer. lwjgl seems to make opengl easy and Object Oriented. threads are new to me though... and games programming requires a good understanding of them. I am doing my BSc in computer science. and thought making little games would help. hmmm.... the data structures are interesting, quad-trees and octa-trees.

---

### Post by t1497f35 on 2011-05-29
OpenGL in essence is hw accelerated nowadays. So if Java is using OpenGL - it does use hw accel.
There are 2 ways one uses / could use OpenGL stuff through Java.
1) Directly - through bindings, like JOGL or other projects out there, it crashed once on me, maybe twice, but it might be stable already.
2) Indirectly - when the java2d uses the OpenGL pipeline (as opposed to the default software/CPU pipeline), so the stuff you draw with swing is actually using OpenGL under the hood which is (much) slower than using OpenGL as in option #1 but is decent for moderate (2D only) games. Since the OpenGL pipeline was created by Sun Microsystems several years ago when the Linux/Unix drivers were in a much more horrible state - Sun never bothered to polish the OpenGL pipeline since it obviously didn't make much sense back then since the OpenGL drivers were too broken anyway - so it still freezes here and there if you switch it on, basically it's not ok to use it. Oracle doesn't bother either updating it  to match the current state of the video drivers on Linux since Oracle doesn't care too much (almost at all) about desktop Java since they're an enterprise/server oriented corporation. What Oracle does though is enable the Xrender extension on Linux starting with Java 7 due to be released this summer (which is a dead-end since in a few years from now X.org will be dumped in favor of Wayland), though last time I checked the weekly build of JDK7 that extension was (still) disabled by default. This extension, unlike the OpenGL pipeline, provides hw acceleration only for a limited number of drawing operations (the most basic ones), but it's still (a lot) better than a sofware only pipeline as it is the case with Java on Linux now.

Regardless, for 2D games Java's current 2D software pipeline might be good enough for you.

---

### Post by Jonas thomas on 2011-05-29
> **vivichrist said:**
> hmm, I have looked at libcluttermm, libgtkglext various canvas libs and clanlib etc. what would be the best graphics library from an object oriented C++ or Java perspective? I want to make small games, graphics demo's in gtk and possibly portable java versions. I don't much like the procedural approach using C to program opengl apps.

My daughter(8) has been wanting me to write her a game.. In the meantime she wants to play funguloids (which is currently broken in synaptic).. 
funguloids is written in C++ and uses Ogre..  She goes Dad... you took a C++ class can't you fix it.. Anyway.. I've been working my way through the Ogre3d tutorials..[http://www.ogre3d.org/tikiwiki/Tutorials]("http://www.ogre3d.org/tikiwiki/Tutorials")
Seems like a good way to improve my  C++ skillsets and have fun doing it.

Its learning curve doesn't seem to be too bad.

---

### Post by vivichrist on 2011-05-30
indeed, and there's a plugin for blender. nice! looks like a very powerful API. tutorials are quite well written too.

---

### Post by vivichrist on 2011-06-28
and so I looked into ogre but ogre either has a bug with linux or doesn't like intel 945 chipset or something... anyway, I started to learn Java3D. as I was confused as to what LWJGL and JOGL were and opengl seemed like a pain to work with. As it turns out there are multiple alternatives to Java3D one which I am exploring currently is Xith3D. so easy, yet so many classes and interfaces looks very promising though, and uses LWJGL or JOGL/AWT as a base for rendering opengl. Java3D has some really inconvenient ways of doing things i.e locking the visual objects and groups unless you change the capabilities of them and a lack of loaders for common 3D file formats or an easy way to access those visual objects once loaded. pain pain pain...

---

### Post by JDShu on 2011-06-29
> **Petrolea said:**
> Yes it was. But the RAM consumption is enormous.

I hear this is more a problem with Notch's code than Java itself.

---

### Post by PaulM1985 on 2011-06-29
I would recommend LWJGL rather than JOGL.  I have tried both and JOGL didn't seem to work on some computers.  LWJGL seems to be fine.

Paul

---

### Post by leg on 2011-06-29
The [Iirlicht]("http://irrlicht.sourceforge.net/") library is very useful for putting together quick interactive environments. Another one I have used in the past is [Ogre]("http://www.ogre3d.org/") which is also very good.

---

### Post by vivichrist on 2011-06-29
One obstacle I am encountering is jadatoo (xith3D's input library). mouse stuff works fine but keyboard, not a sausage. and this is with the tutorial code straight from xin (xith in a nutshell). which I swear it has an input focus problem that doesn't happen on the windows side of things. but seeing as I can't find any object to call request focus on, I really don't know what to do.

---


---
title: "irrlicht"
date: 2007-01-15
forum: Programming Talk
---

### Post by Choad on 2007-01-15
how would i go about getting started with this 3d engine + ubuntu?

any tips/comments welcome

ide?

---

### Post by Wybiral on 2007-01-15
Download the package, go to one of the example folders and try the Makefile. I've gotten a number of them to work, but sometimes they require some tweeking.

I've only tried the SDK 1.1 on ubuntu... I don't know if 1.2 works, but it should.

---

### Post by amo-ej1 on 2007-01-16
in a distant past i once played with irrlicht and i simply followed the tutorials on their site, and it was amazing how fast you could get very nice results.

---

### Post by Choad on 2007-01-16
i look forward to it then

does it have a physics engine? i know it has an animation engine...

ever played armoured core? i want to make a game similar to that, but with added physics. uber customisation, with the potential to blow limbs off and knock the robots over

this is obviously a long way in the future when i am more experienced. for the moment i'd settle with anythng to shut my computing teacher up about visual studio. hes such a microsoft fanboy its painful. (edit: i do like vs2k5 tho :) its great)

---

### Post by amo-ej1 on 2007-01-16
The features are at [http://irrlicht.sourceforge.net/features.html](http://irrlicht.sourceforge.net/features.html)

no physics in that list ;). But irrlicht is only a 3d engine, so only focusing on graphics (you're lucky they even throw collision detection with it). So you're responsible for things like physics, audio and ai yourself.

---

### Post by Choad on 2007-01-16
oh one more thing

i understand programmers, especially the more hardcore programmers, prefer irc over forums for helping each other.

correct?

anyhow, i have NEVER used irc before, so could you advise me on a client and where to go for irrlicht discussion, and general programming discussion (c++) etc. i would apprieciate it :D

---

### Post by amo-ej1 on 2007-01-16
irc clients are easy, use xchat, irssi, gaim or bitchx to connect to IRC. The general suport for a package is usually listed on their webpage.

But there's a great deal of support on other location too developer forum (guess where you are right now :p, and you're getting support aren't you ?), there's an irrlicht forum, a wiki, probably a mailing list too ...

---

### Post by Choad on 2007-01-16
```
richard@richard-laptop:~/Desktop/irrlicht-1.2/examples/01.HelloWorld$ make
g++ main.cpp -o example -I"../../include" -I"/usr/X11R6/include" -L"/usr/X11R6/lib" -L"../../lib/Linux" -lIrrlicht -lGL -lGLU -lXxf86vm -lXext -lX11
/usr/bin/ld: cannot find -lXxf86vm
collect2: ld returned 1 exit status
make: *** [all] Error 1

```

what do i need to get to allow the first example to compile?

---

### Post by Choad on 2007-01-16
never mind, i figured this out

some of the tutorials work, but most of them fail with no error description

```
richard@richard-laptop:~/Desktop/irrlicht-1.2/examples/07.Collision$ cd ../08.SpecialFX/
richard@richard-laptop:~/Desktop/irrlicht-1.2/examples/08.SpecialFX$ make
g++ main.cpp -o example -I"../../include" -I"/usr/X11R6/include" -L"/usr/X11R6/lib" -L"../../lib/Linux" -lIrrlicht -lGL -lGLU -lXxf86vm -lXext -lX11
richard@richard-laptop:~/Desktop/irrlicht-1.2/examples/08.SpecialFX$ ./example 
Please press 'y' if you want to use realtime shadows.
y
Please select the driver you want for this example:
 (a) Direct3D 9.0c
 (b) Direct3D 8.1
 (c) OpenGL 1.5
 (d) Software Renderer
 (e) Burning's Software Renderer
 (f) NullDevice
 (otherKey) exit

c
Irrlicht Engine version 1.2
Linux 2.6.17-10-generic #1 SMP Fri Dec 15 02:09:09 CET 2006 i686
Using renderer: OpenGL 2.1.0
GeForce Go 7600/PCI/SSE2: NVIDIA Corporation
OpenGL driver version is 1.2 or better.
Loaded mesh: ../../media/room.3ds
Loaded texture: ../../media/wall.jpg
Loaded texture: ../../media/stones.jpg
Loaded texture: ../../media/water.jpg
Loaded texture: ../../media/particlewhite.bmp
Loaded texture: ../../media/fire.bmp
Loaded texture: ../../media/axe.jpg
Loaded texture: ../../media/dwarf.jpg
Could not open file of texture: ../../media/dwarf2.jpg
Could not open file of texture: dwarf2.jpg
Loaded mesh: ../../media/dwarf.x
pure virtual method called
terminate called without an active exception
Aborted (core dumped)

```

i was just going through each example, compiling and executing. only 3 or 4 worked... most errored like this....

---

### Post by Wybiral on 2007-01-16
Yeah... I had the same problem. The textures in the bsp don't exist! Go ahead and make a copy of the dwarf image and name it dwarf2, it solves that problem... But there are more exceptions after this. You can probably get around this by creating your own level to load and actually having all of the resources, I'm not entirely sure why the heck they did that... Or why it works on windows and now linux **shrug**

Unless there's an "ignore exceptions" flag or something I missed.

---

### Post by Choad on 2007-01-16
done, still get the same error!

laaame.

its wired, the individual examples often dont work, but the last example, with particles, lighting and input does work. the individual examples didnt. how odd....

---


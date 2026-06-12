---
title: "Having trouble installing GLUT"
date: 2010-05-23
forum: Programming Talk
---

### Post by jason102 on 2010-05-23
Hi guys,

So a day ago I wiped the disk clean and installed 10.04 - and so far everything's going fine.

However, for some reason I can't get glut and its development files installed correctly. I'm currently working on an OpenGL app in C++, and I require the use of glut for it. 

I'm using g++ as a compiler for this project, so I installed that first (it installed fine), and then I tried installing glut. As is suggested, I installed freeglut3 and freeglut3-dev, but I still get tons of compile time errors for all the "glu..." commands in my code. 

Now that I think of it, I'm not seeing any errors for the "glut..." commands, just the "glu..." ones. I checked, and libglu1-mesa and libglu1-mesa-dev are both installed (I think they're installed along with freeglut3).

I'm getting a bunch of undefined references to ... errors, meaning g++ can't find the GLU development files on my machine, even though you would think Synaptic should have set that all up for me?

A few days earlier when I was still using 9.10 everything was compiling fine - I haven't changed any of the code since then.

Any ideas? Do I need to install something more so this can work on 10.04? Thanks!

---

### Post by splicerr on 2010-05-24
You're being rather vague IMO. I think it would be more helpful if you just give the comand you use to compile and the error messages itself.

---

### Post by jason102 on 2010-05-24
> **splicerr said:**
> You're being rather vague IMO. I think it would be more helpful if you just give the comand you use to compile and the error messages itself.

Hey, if you want a print out of these errors, here they are - like I said, they're all "undefined reference to..." errors complaining about glu commands:

```
jason@jason-desktop:~/476/trunk$ make
g++ -lglut -o Helios BaseProgram.o Camera.o Display.o Helios.o Utility.o text3d.o Tunnel.o UI.o Unit.o Model.o DataWarden.o MainMenu.o Obstacle.o main.o Communication.o Timers.o Menu.o
Camera.o: In function `Camera::look() const':
/home/jason/476/trunk/Camera.cpp:24: undefined reference to `gluLookAt'
Tunnel.o: In function `TunnelJoint::draw(Tuple<3, float> const&, int) const':
/home/jason/476/trunk/Tunnel.cpp:79: undefined reference to `gluNewQuadric'
/home/jason/476/trunk/Tunnel.cpp:80: undefined reference to `gluQuadricNormals'
/home/jason/476/trunk/Tunnel.cpp:98: undefined reference to `gluSphere'
/home/jason/476/trunk/Tunnel.cpp:107: undefined reference to `gluDeleteQuadric'
Tunnel.o: In function `Tunnel::drawHalf(TunnelJoint const*, Tuple<3, float> const&, int) const':
/home/jason/476/trunk/Tunnel.cpp:166: undefined reference to `gluNewQuadric'
/home/jason/476/trunk/Tunnel.cpp:167: undefined reference to `gluQuadricNormals'
/home/jason/476/trunk/Tunnel.cpp:217: undefined reference to `gluCylinder'
/home/jason/476/trunk/Tunnel.cpp:228: undefined reference to `gluDeleteQuadric'
Unit.o: In function `LightLaserAttacker::innerDraw(Tuple<3, float> const&, int) const':
/home/jason/476/trunk/Unit.cpp:278: undefined reference to `gluNewQuadric'
/home/jason/476/trunk/Unit.cpp:279: undefined reference to `gluCylinder'
/home/jason/476/trunk/Unit.cpp:282: undefined reference to `gluDeleteQuadric'
Unit.o: In function `Digger::innerDraw(Tuple<3, float> const&, int) const':
/home/jason/476/trunk/Unit.cpp:257: undefined reference to `gluNewQuadric'
/home/jason/476/trunk/Unit.cpp:261: undefined reference to `gluCylinder'
/home/jason/476/trunk/Unit.cpp:263: undefined reference to `gluDeleteQuadric'
MainMenu.o: In function `MainMenu::initMenuScreen(Screen const&) const':
/home/jason/476/trunk/MainMenu.cpp:127: undefined reference to `gluOrtho2D'
Obstacle.o: In function `Rock::draw(Tuple<3, float> const&, int) const':
/home/jason/476/trunk/Obstacle.cpp:12: undefined reference to `gluNewQuadric'
/home/jason/476/trunk/Obstacle.cpp:13: undefined reference to `gluQuadricNormals'
/home/jason/476/trunk/Obstacle.cpp:14: undefined reference to `gluSphere'
/home/jason/476/trunk/Obstacle.cpp:15: undefined reference to `gluDeleteQuadric'
Obstacle.o: In function `Resource::draw(Tuple<3, float> const&, int) const':
/home/jason/476/trunk/Obstacle.cpp:36: undefined reference to `gluNewQuadric'
/home/jason/476/trunk/Obstacle.cpp:37: undefined reference to `gluQuadricNormals'
/home/jason/476/trunk/Obstacle.cpp:38: undefined reference to `gluSphere'
/home/jason/476/trunk/Obstacle.cpp:39: undefined reference to `gluDeleteQuadric'
Menu.o: In function `UI::initMenuScreen(Screen const&) const':
/home/jason/476/trunk/Menu.cpp:855: undefined reference to `gluOrtho2D'
Menu.o: In function `UI::displayDirection() const':
/home/jason/476/trunk/Menu.cpp:750: undefined reference to `gluNewQuadric'
/home/jason/476/trunk/Menu.cpp:751: undefined reference to `gluQuadricNormals'
/home/jason/476/trunk/Menu.cpp:763: undefined reference to `gluSphere'
/home/jason/476/trunk/Menu.cpp:766: undefined reference to `gluCylinder'
/home/jason/476/trunk/Menu.cpp:771: undefined reference to `gluSphere'
/home/jason/476/trunk/Menu.cpp:777: undefined reference to `gluSphere'
/home/jason/476/trunk/Menu.cpp:780: undefined reference to `gluDeleteQuadric'
Menu.o: In function `UI::displayHemisphere(bool) const':
/home/jason/476/trunk/Menu.cpp:712: undefined reference to `gluNewQuadric'
/home/jason/476/trunk/Menu.cpp:713: undefined reference to `gluQuadricNormals'
/home/jason/476/trunk/Menu.cpp:737: undefined reference to `gluSphere'
/home/jason/476/trunk/Menu.cpp:743: undefined reference to `gluDeleteQuadric'
collect2: ld returned 1 exit status
make: *** [Helios] Error 1
jason@jason-desktop:~/476/trunk$ 
```

---

### Post by splicerr on 2010-05-24
-lGLU

---

### Post by jason102 on 2010-05-24
> **splicerr said:**
> -lGLU

Yeah, I was thinking about that too, but nope, that didn't fix it. At first the only place -lGLU is defined is on the LDFLAGS_CYG line, for our Cygwin users I presume. I just added -lGLU to the first LDFLAGS line in our Makefile but it didn't change anything. This is what the top of this Makefile looks like:

```
UNAME := $(shell uname -s)
CC=g++
CFLAGS=-Wall -g -pedantic -Wno-variadic-macros
LDFLAGS=-lglut -lGLU
LDFLAGS_MAC=-framework OpenGL -framework GLUT -lm
LDFLAGS_CYG=-L/lib -lglut -lGLU -lGL -lm
ALL=Helios
```

By the way, I'm on a team, and someone else is managing this Makefile, so I'm not completely sure about how it works or is setup - I'm still a newbie when it comes to Makefiles. 

Still, my general computer knowledge and intellect is strongly hinting at these libraries not being installed correctly.

Any more ideas?

---

### Post by jason102 on 2010-05-24
Hold on, ok, I think I got it working - adding in -lGLU actually worked. 

That's strange - do we now need to specify -lGLU in 10.04? Like I said, I never modified this code until now, and it was compiling just fine on 9.10...

Nonetheless, I'll let this other guy on the team know that the Makefile must be updated for all of us. There are other members of the team who are using Ubuntu to develop this on, so they'll need to know that updating to the latest OS could be requiring something new.

Or else I'm still completely wrong with that notion...?

In any case, that fixed it - thanks splicerr!

---

### Post by psychok7 on 2010-05-25
> **splicerr said:**
> -lGLU

sweet that also worked for me.. but i would also like to know why this new flag on ubuntu 10.04

---

### Post by soltanis on 2010-05-25
If you added -lGLU to your LD_FLAGS but that didn't solve your problem, then it's possible your makefile was written incorrectly and is not incorporating the variable into its invocation of ld, or otherwise some other problem. Since you don't maintain the makefile yourself, you can happily absolve yourself of this concern: email the guy who does maintain it and tell him that your system now requires explicitly linking GLU, and if he'd kindly update the makefile.

Hurrah for responsibilities.

---

### Post by splicerr on 2010-05-26
> **psychok7 said:**
> sweet that also worked for me.. but i would also like to know why this new flag on ubuntu 10.04

My guess is that before 10.04 libglut was linked against libGLU, so you got lucky. In general it's best practice to add the necessary linker flags for every libraries you're using symbols of.

---


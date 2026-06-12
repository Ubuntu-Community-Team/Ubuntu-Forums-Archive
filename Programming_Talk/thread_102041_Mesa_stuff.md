---
title: "Mesa stuff"
date: 2005-12-11
forum: Programming Talk
---

### Post by matthewb on 2005-12-11
Hello... I'm new in Mesa... When i tried to compile (using "gcc -l glut foo.c -o foo") progs in my Ubuntu 5.10 at home it did'nt work... I checked and found out that libGL.so.1, libGL.so.1.0.7667, libGLU.so.1, libGLU.so.1.3.060302, libglut.so.3 and libglut.so.3.8.0 are already there...specifically in the /usr/lib directory.Though already there, I run apt-install mesa-utils but I got the ff messages:
         Reading package lists...
         Building dependency tree...
         mesa-utils is already the newest version
         0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded 
which I believe means that Mesa is already installed... What happened? What's wrong? Please help...

---

### Post by thumper on 2005-12-11
Saying something didn't work is not overly helpful when talking about compilers.

You'd need to post the output from the compile command.

---

### Post by matthewb on 2005-12-12
Hello a friend of mine said that I most likely have to install
something with a (mesa-something)-dev to denote the development part for the library... Is it safe for me run the progs after? Thanks...

---

### Post by thumper on 2005-12-12
Well, what is the error that you are getting?

---


---
title: "gcc can't find Xt?"
date: 2009-02-24
forum: Packaging and Compiling Programs
---

### Post by s1337m on 2009-02-24
Building ../../../bin/sum
/usr/bin/ld: cannot find -lXt
collect2: ld returned 1 exit status
make[1]: *** [../../../bin/sum] Error 1
make: *** [dep] Error 2

I've installed x11-dev... and tried googling around to find this library.  How can I grab this lib?  I'm on hardy heron

---

### Post by snova on 2009-02-24
Install the **libxt-dev** package.

---

### Post by s1337m on 2009-02-24
thanks for the help, that resolved that missing library.  But now I am trying to find the -GL library, I assume thats the opengl.  When I try to sudo apt-get install libgl-dev, i get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgl-dev is a virtual package provided by:
  libgl1-mesa-swx11-dev 7.0.3~rc2-1ubuntu3
  libgl1-mesa-dev 7.0.3~rc2-1ubuntu3
You should explicitly select one to install.
E: Package libgl-dev has no installation candidate


Which package should I install?  (Also I have drivers already in use for 3d acceleration on my ati radeon)

---

### Post by snova on 2009-02-25
Definitely **libgl1-mesa-dev**. The other one appears to be part of a variant that is incapable of hardware acceleration. You probably don't even have it installed.

---


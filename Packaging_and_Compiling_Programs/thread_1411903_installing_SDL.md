---
title: "installing SDL"
date: 2010-02-20
forum: Packaging and Compiling Programs
---

### Post by worksofcraft on 2010-02-20
I want to start programing multi-media applications and gather a good place to start is with the SDL (Simple DirectMedia Layer) libraries.

I tried:
sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev

...result:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl-mixer1.2-dev: Depends: libvorbis-dev but it is not going to be installed
  libsdl-ttf2.0-dev: Depends: libfreetype6-dev but it is not going to be installed
  libsdl1.2-dev: Depends: libx11-dev but it is not going to be installed
                 Depends: libglu1-mesa-dev but it is not going to be installed
                 Recommends: libxt-dev but it is not going to be installed
                 Recommends: libxext-dev but it is not going to be installed
                 Recommends: libaa1-dev but it is not going to be installed
                 Recommends: libdirectfb-dev (>= 0.9.22) but it is not going to be installed
E: Broken packages

-----

What would be the right way to get this SDL library installed?

---


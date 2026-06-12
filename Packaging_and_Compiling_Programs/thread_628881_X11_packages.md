---
title: "X11 packages"
date: 2007-12-01
forum: Packaging and Compiling Programs
---

### Post by divisortheory on 2007-12-01
Hi, I'm a little new to Linux.

I'm trying to compile some programs with dependencies on X11, but it cannot find the X11 header or library files anywhere.  What package are these in?

Also, is there a searchable reference somewhere that has a list of all packages that are available and what they are?

---

### Post by Vicfred on 2007-12-02
im having similar problem when i try to compile from source it says it cannot find the x11 development files :(

well i thinks its pretty obvious but im newbie on compiling from source i've just compiled x264 with a step by step guide >O<

---

### Post by dholbach on 2007-12-03
What is the error message?

X was split up into lots of individual smaller packages, so there is no such thing as a "X Development package", GTK for example build-depends on these X related development packages  [...] libx11-dev (>= 2:1.0.0-6), libxext-dev, libxi-dev, libxrandr-dev, libxt-dev, libxrender-dev, libxft-dev, libxcursor-dev, libxcomposite-dev, libxdamage-dev, libxkbfile-dev, libxinerama-dev, libxfixes-dev, x11proto-xext-dev [...]

---


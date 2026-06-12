---
title: "OGG/Vorbis Linking Problems"
date: 2008-04-26
forum: Packaging and Compiling Programs
---

### Post by FlyingIsFun1217 on 2008-04-26
Hey!

Trying to compile Torque on Linux. The only problem I am having is with the linking of the ogg/vorbis libraries.

Torque is supposed to link to libraries automatically, but it seems to be having some problems with these two. Were their locations changed to something unconventional in Hardy?

Thanks!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-04-27
Somebody's got to know whats going on here...

It linked just fine in Gutsy and Feisty.

FlyingIsFun1217

---

### Post by Compyx on 2008-04-27
Posting the output of the script you're using to compile the program would help. I assume the libraries you need are already installed (libogg-dev and libvorbis-dev from what I can tell).

---

### Post by FlyingIsFun1217 on 2008-05-03
Well, I've seemed to fix it. The makefile for Torque was looking for the libraries in /lib/xiph/ (I believe), when it should have been looking in /usr/lib.

Thanks!
FlyingIsFun1217

---


---
title: "Help!!!! Qt???"
date: 2009-01-05
forum: Programming Talk
---

### Post by Tony Romo on 2009-01-05
I've been trying to learn C++ GUI programming and want to install QT to work with g++ but it dosen't seem to find the header files after I install it. Any help will be MUCH appreciated! :confused:

---

### Post by pansz on 2009-01-05
did you installed QT properly?

if not, try the following command:

sudo apt-get build-dep kdebase

---

### Post by samjh on 2009-01-05
sudo apt-get install qt4-dev-tools

Make sure you are compiling your Qt programs properly.

qmake -project
qmake
make

Consult the Qt tutorial for step-by-step lessons:
[http://doc.trolltech.com/4.4/tutorials-tutorial.html](http://doc.trolltech.com/4.4/tutorials-tutorial.html)

---


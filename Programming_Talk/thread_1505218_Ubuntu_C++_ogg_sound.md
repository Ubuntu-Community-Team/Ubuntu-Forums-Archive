---
title: "Ubuntu C++ ogg sound"
date: 2010-06-08
forum: Programming Talk
---

### Post by ownsuall on 2010-06-08
How would you play an ogg file via c++ in ubuntu?

---

### Post by Axos on 2010-06-08
The quick 'n' dirty way is to fork and exec a program like /usr/bin/paplay to play the file for you.

If you prefer to do it the hard way (and have more control), take a look at:

[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

Edit: I should have explained that the gstreamer runtime libraries are already included with Ubuntu. To compile programs which use gstreamer you'll need to install the development package (libgstreamer0.10-dev, I believe).

---

### Post by ownsuall on 2010-06-09
Yeah but i doesn't look like it can do 3d sound.. I need 3d sound for my project though.

---


---
title: "What have I done?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by jeff Odom on 2008-09-23
I've just recently downloaded Ubuntu, but when I pick it as the O.S. I want it just goes to what seems to be a DOS prompt asking for my username and password, but after that does not go to a desk top. What have I done wrong?

---

### Post by mevets on 2008-09-23
did you download and install the server version? You can tell if when you installed you never got a full desktop, but only a text installer (this applies to server and  alternate).

Try running 'startx' which should start the desktop stuff if its installed.

The desktop version can be downloaded from here: [http://ubuntu.media.mit.edu/ubuntu-releases/hardy/ubuntu-8.04.1-desktop-i386.iso](http://ubuntu.media.mit.edu/ubuntu-releases/hardy/ubuntu-8.04.1-desktop-i386.iso)

---

### Post by jken146 on 2008-09-23
To check if you've installed the server version, type ```
uname -r
```  If it says something like 2.6.24-19-server then you've got the server version; if it says something like 2.6.24-19-generic, you've got the desktop version.

If you have installed the server version, just type ```
sudo apt-get install ubuntu-desktop
``` to install the graphical bits.

---


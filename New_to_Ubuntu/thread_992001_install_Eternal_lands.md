---
title: "install Eternal lands"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by lokidarcus on 2008-11-24
i can not get eternal land to install i have the file unziped on my desktop but i do not know ha to get it to install:confused:

---

### Post by ggaaron on 2008-11-24
Can't you use synaptic (System->Administration->Synaptic in menu I believe)?

---

### Post by lokidarcus on 2008-11-25
how whoud i install it like that?

---

### Post by gandaran on 2008-11-25
did you download the correct file for linux? .bin?
follow the instructions on web site
> To play on Linux (generic distro):
Download the zip file, and unzip it.
cd to the directory where you installed it.
There are two .bin files, on for 32b and the other for 64b. Depending on your platform, chmod the binary to 775, and execute it.
Edit el.ini and change datadir to where you unzip everything
The default base directory is called el_install, and you might want to rename it to something else.
or simply right click the file, go to properties, permission tab, tick the execute box  then cd the terminal to the folder where the file is and type
**./'name of file to install or run'** use sudo if it needs root permission

or use a synaptic repository install, see this link for ubuntu [https://help.ubuntu.com/community/EternalLands](https://help.ubuntu.com/community/EternalLands)

---

### Post by ggaaron on 2008-11-25
This help.ubuntu.com/... seems to be a nice guide how to install this software cleanly with synaptic, you should try it.

Sorry for my previous post, I was quite sure that this game was in the default tree, but it isn't.

---


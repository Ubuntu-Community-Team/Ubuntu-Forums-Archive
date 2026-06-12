---
title: "help with vpython"
date: 2005-07-20
forum: Programming Talk
---

### Post by jsvidyad on 2005-07-20
Hi!!

I installed vpython yesterday on my computer. It was working fine initially. But, today when I tried to run programs using vpython, it was giving an error message saying:

OpenGL initialization failed.
Unable to create OpenGL display widget

I don't know why this problem has suddenly cropped up. By the way, vpython is working fine on my windows partition.

---

### Post by lgiomi on 2005-08-01
Hey, how did you do that?

I've been trying to install vpython for a while, but I cannot fix a problem
related with the location of some gtkglarea headers (at least this is 
what I guess). The configure scrip crashes with the following error 
message:

[B]checking for GTK - version >= 0.99.7... yes
checking for gdk_gl_query in -lgtkgl... no
configure: error: gtkglarea is required on Unix-like systems[/B]

 ](*,)  Help please!

- Luca

---

### Post by margido on 2005-09-04
Try:


 install/check for:

# python-dev
# python-numeric
# gtkglarea5-dev
# libgtk1.2-dev
# g++
# libboost-python-dev
# xlibmesa-glu-dev
# idle 

download and untar:

tar -xjf visual-3.2.1.tar.bz2

install:

 ../visual-3.2.1/configure

make

sudo make install 

test:

$ cd /usr/local/lib/python2.4/site-packages/visual/examples
$ python hanoi.py

more info at:

[http://www.aims.ac.za/wiki/index.php/Vpython](http://www.aims.ac.za/wiki/index.php/Vpython)

---

### Post by toships on 2005-10-07
Hi

I am trying to install vpython on Breezy and followed the steps in the previous post. 

I could not install xlibmesa, it says packet not found. 

When I install vpython and try to run an example it gives the following error. 

----------
Xlib:  extension "GLX" missing on display ":0.0".

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkWidget'
OpenGL initialization failed.
----------

I also tried the package python-visual but it gives the same error.

Please help.
Thanks.

---

### Post by lgiomi on 2005-10-21
Don't make your life harder. On Breezy you can install vpython as a standard package with apt.

- Luca

---


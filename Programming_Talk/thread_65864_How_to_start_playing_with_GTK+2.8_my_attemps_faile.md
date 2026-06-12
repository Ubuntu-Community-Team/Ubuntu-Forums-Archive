---
title: "How to start playing with GTK+2.8 my attemps failed"
date: 2005-09-15
forum: Programming Talk
---

### Post by coulix on 2005-09-15
hello,
First i tried to install all the packaged related close or far or gtk programming with synaptics, then i tried to start a gtk+ c and gtkmm c++  project with Anjuta.

however it doesnt recognise this :  #include <gtk/gtk.h>

Then i went on Gtk website followed the istruction and get it compiling
from command line with : g++ base.c -o base `pkg-config --cflags --libs gtk+-2.0`

what is this `pkg-config --cflags --libs gtk+-2.0` ?
Do i had to really install the gtk tolkit from sources like a did (make make install)
or it is anywhere in the ubuntu repository,

If i wan to make it compile straight in anjuta wiht   #include <gtk/gtk.h>,
how can i do ?

thank you

---

### Post by tageiru on 2005-09-15
libgtk2.0-dev is the package in ubuntu with the devlopment files for gtk.

pkg-config is a nifty program that finds the correct includes, cflags and libraries to use for compilation.

---


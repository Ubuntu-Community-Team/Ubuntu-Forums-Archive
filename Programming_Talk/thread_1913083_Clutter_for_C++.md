---
title: "Clutter for C++"
date: 2012-01-21
forum: Programming Talk
---

### Post by vanangamudi on 2012-01-21
I cannot find cluttermm library (clutter equivalent) for C++. Hav to add any repository?

---

### Post by bouncingwilf on 2012-01-22
libclutter is in the repos, cluttermm should be obtainable from
[http://ftp.gnome.org/pub/GNOME/sources/cluttermm/](http://ftp.gnome.org/pub/GNOME/sources/cluttermm/)


Bouncingwilf

---

### Post by vanangamudi on 2012-01-22
I hav downloaded that already. how to develop my application with that. I mean how could use it for my wish.

---

### Post by vanangamudi on 2012-01-22
I hav downloaded that already. how to develop my application with that. I mean how could use it for my wish.  Can u help me to setup the development environment and to compile any other opensource projects as a development package. like libclutter-_dev_ for "C"...

---

### Post by bouncingwilf on 2012-01-22
I'm not sure what you have done with the downloaded file but this is what I'd do

1.) Download the latest sources cluttermm-1.3.3.tar.bz2
2.) unpack this file into a clean directory
3.) Read the file INSTALL and follow the instructions ( this is the normal Linux practice).

 Basically, the standard ./configure make and sudo make install should install the libraries and then you need to just link to them in your project ( I presume -lcluttermm should do it but you will need to read the documentation.)

Bouncingwilf

---


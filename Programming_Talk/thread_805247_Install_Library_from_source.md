---
title: "Install Library from source"
date: 2008-05-23
forum: Programming Talk
---

### Post by MicahCarrick on 2008-05-23
I'm not sure the "best" or conventional way to install a library from source that much of my system is dependent upon.

Say for example, I wanted to remove glib and install it from source instead. How can I remove the libglib package before installing from source to ensure there is no conflicts? If I try to remove it with aptitude, it'll also try to remove all packages dependent upon glib. 

If another package is later installed from aptitude that requires glib, will it not recognize that it's already been installed from source?

---

### Post by pdwerryhouse on 2008-05-23
If you want to try out a different version of libglib, you're better off installing it to a different location (eg, under /usr/local, or better, /usr/local/libglib) where it won't interfere with the rest of the system.

There are ways to remove packages without taking all the dependent programs with them (eg, dpkg -r --force-depends) but this will break your system and cause you considerable pain.

The easiest way to compile up the library and install it in a different location is to give the --prefix option to configure when building it.

Eg, something like this:

./configure --prefix=/usr/local/libglib
make
make install

---


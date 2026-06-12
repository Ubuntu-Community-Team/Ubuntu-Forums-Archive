---
title: "problem on installing qt"
date: 2011-11-13
forum: Packaging and Compiling Programs
---

### Post by rinosalman on 2011-11-13
hi...
thanks to guide me before..
i tried install qt on my ubuntu..this the step..
run " ./configure -libdir /usr/local/lib -bindir /usr/local/bin -headerdir /usr/local/include/qt "
and then i got "Qt is now configured for building. Just run make.
To reconfigure, run make clean and configure."
i ran make..but i got " In file included from kernel/qinputcontext_p.h:53,
                                                       from kernel/qapplication_x11.cpp:78:
kernel/qt_x11.h:79: fatal error: X11/extensions/shape.h: No such file or directory "
i tried find an answer by googling, the answer was asked me to install x-dev, but when i typed "sudo apt-get -y install x-dev", i found this
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package x-dev
thanks for reading, i appreciate any kind of help that can be given

---


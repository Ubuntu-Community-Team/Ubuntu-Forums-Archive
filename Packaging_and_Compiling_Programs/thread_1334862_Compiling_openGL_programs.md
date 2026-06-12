---
title: "Compiling openGL programs"
date: 2009-11-22
forum: Packaging and Compiling Programs
---

### Post by cbabbage on 2009-11-22
I'm using Ubuntu8.04 and have started writing openGL programs. However when I attempted to compile, I found that `pkg-config --cflags --libs gl` doesn't work. I haven't found anything useful elsewhere on the subject. So, does anyone know how to get pkg-config to work for openGL, or any other method to get the dependencies needed to compile openGL programs. 

Thanks in advance for any help.
CB.

---

### Post by SevenMachines on 2009-11-23
`pkg-config --cflags --libs gl` works on 9.10 but its possible it wasnt set up in 8.04, pkg-config only returns -lGL though, which is what you want to add to the compiler parameters to allow the linker to work. 

on 9.10 for example you would install,
libgl1-mesa-dev, this contains the pkg-config files amongst other things, it also depends on
mesa-common-dev, which has the opengl header files, which you should find in /usr/include/GL so
#include <GL/gl.h>

---

### Post by cbabbage on 2009-11-23
Okay, problem solved by using -lGL. Thanks very much.
CB

---


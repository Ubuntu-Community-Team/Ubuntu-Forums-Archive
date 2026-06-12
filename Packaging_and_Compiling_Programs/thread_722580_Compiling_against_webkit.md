---
title: "Compiling against webkit"
date: 2008-03-12
forum: Packaging and Compiling Programs
---

### Post by gmclachl on 2008-03-12
Hi I am trying to compile a small c program which use the Webkit headers. I have libwebkit-dev installed and the header files are in /usr/include/Webkit

However when I try to compile  using 

 gcc lwb.c -o lwb `pkg-config --cflags gtk+-2.0` 

I get 

 error: Webkit/webkit.h: No such file or directory

I can't use pkg-config as it's too low a version shipped with ubuntu. 

Thanks
George

---


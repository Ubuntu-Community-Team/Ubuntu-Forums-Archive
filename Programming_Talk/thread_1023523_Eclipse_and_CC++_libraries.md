---
title: "Eclipse and C/C++ libraries"
date: 2008-12-28
forum: Programming Talk
---

### Post by nebu on 2008-12-28
I am not very adept at using Eclipse.... i have just installed the c/c++ development tools for eclipse....

i am having a bit of a problem using the c/c++ libraries.... how do you tell eclipse which libraries to use....

for example how do i tell eclipse to include math.h or sdl or iostream.h or netdb

---

### Post by jbrackett on 2008-12-28
I don't have eclipse sitting in front of me but I found a picture

[http://www.flickr.com/photos/ebothy/3065842066/in/set-72157610334328256/](http://www.flickr.com/photos/ebothy/3065842066/in/set-72157610334328256/)

I believe you get this menu by right clicking on your project and choosing properties.  Choose the libraries section and add in whatever you would have after the -l if compiling from the terminal (-lm, -lX11, etc)

---


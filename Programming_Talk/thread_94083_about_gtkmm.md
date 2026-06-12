---
title: "about gtkmm"
date: 2005-11-23
forum: Programming Talk
---

### Post by newen on 2005-11-23
I´ve been always a c++ guy, and changing my mind to program with gtk is really hard! hehe
I´ve been thinking about moving to gtkmm. But there are many thins that I would like to know:

 How about the performance? we´ll this is not very important for desktop apps, but when gtkmm is used, more lib depedencies are added and more libraries to be loaded...

Well, second point: why the latest version in the repositories is 2.4 and not the latest stable 2.8 (even in the debian repositories). gtkmm is a wrapper for gtk 2.4, isn´t?  so, there is no gtk 2.8 support?

More questions to be added ;)

---

### Post by Roptaty on 2005-11-23
First point: Yes, your program will be *slower* than using gtk+, since gtkmm is actually a wrapper around gtk. Loading of libraries happens only at startup time, so in this case, the startup time will increase. However, I don't believe that this slowdown will be significant for normal desktop apps. 


About your second point... Check the version again. :) Even if the package name is gtkmm2.4, it is really 2.8 version. (Use synaptic and check it out.) :)  

[http://packages.ubuntu.com/breezy/libdevel/libgtkmm-2.4-dev](http://packages.ubuntu.com/breezy/libdevel/libgtkmm-2.4-dev)

---

### Post by newen on 2005-11-23
Ok, thanks for the info!

---

### Post by dogen on 2005-11-24
I haven't tried it yet, but there's another library for using gtk with c++ - XFC. 
Look at [http://xfc.xfce.org/docs/index.html](http://xfc.xfce.org/docs/index.html).

Seems to be well supported. Maybe somebody who's had experience with it can post  a few lines.

---


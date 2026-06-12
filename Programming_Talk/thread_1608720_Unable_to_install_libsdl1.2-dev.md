---
title: "Unable to install libsdl1.2-dev"
date: 2010-10-29
forum: Programming Talk
---

### Post by Christian Knudsen on 2010-10-29
I'm on Ubuntu 10.04 and am trying to install libsdl1.2-dev, but I'm running into some dependency problems:

libsdl1.2-dev:
  Depends: libsdl1.2debian (=1.2.14-4ubuntu1) but 1.2.14-4ubuntu1.1 is to be installed
 Depends: libglu1-mesa-dev but it is not going to be installed

What can a poor ol' programmer do?

---

### Post by thomas9459 on 2010-10-29
Try installing libglu1-mesa-dev and try again. It may be it doesn't want to automatically install it.

---

### Post by gmargo on 2010-10-29
Sounds like your lists are out of date, and/or you haven't updated your installation.  Have you done an "apt-get update" or "aptitude update" or updated through a gui package manager (and then a full upgrade)?

---

### Post by Christian Knudsen on 2010-10-29
I didn't really want to do a full upgrade since I'm using an older version of GIMP that is dependent on some older packages, so I've instead just installed Ubuntu 10.10 as a virtual machine running under 10.04. I had no problems installing lidsdl1.2-dev in that virtual machine, so I'll just use that for compiling. Anyway, thanks for the replies. :)

---


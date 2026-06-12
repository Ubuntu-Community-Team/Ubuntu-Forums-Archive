---
title: "writing an 'install' rule for make"
date: 2009-01-22
forum: Packaging and Compiling Programs
---

### Post by Stochastic on 2009-01-22
So I'm brand new to makefiles and I'm in the process of packaging XWAX [http://www.xwax.co.uk](http://www.xwax.co.uk) for Ubuntu, but the makefile has no install rule.  What am I ever to do?  Can anyone point me in the right direction on this one?

---

### Post by plugwash on 2009-01-22
How are you normally supposed to install this program. 

You need to make the install target in debian/rules do what you would normally do when installing the program (including setting up permissions) but rather than installing to the normal place you install to a tree under debian/<binary package name>

---


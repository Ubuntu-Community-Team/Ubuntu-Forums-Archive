---
title: "The problem with an installation in the Gwibber."
date: 2011-07-04
forum: Packaging and Compiling Programs
---

### Post by rsajdok on 2011-07-04
I downloaded the Gwibber by using this:
$ bzr branch lp:gwibber
I read the install file: INSTALL. So I install the Gwibber from source:
$ sudo python setup.py build
$ sudo python setup.py install
I try to run Gwibber:
gwibber/bin$ ./gwibber

In log file of Gwibber I see:
2011-06-23 Gwibber GNOME Client - INFO - Running from the source tree
2011-06-23 Gwibber Service - INFO - Running from the system path

Why the service runs from the system path instead from the source path?

---


---
title: "help with compile errors"
date: 2007-12-11
forum: Packaging and Compiling Programs
---

### Post by DFord425 on 2007-12-11
I am getting compile errors in the C standard libaries, like stdio.h for example and others.  Does anyone know what i can do to fix this other than going into the .h files and changing them (im getting a lot of errors)

---

### Post by dholbach on 2007-12-12
Without a log file it's a bit hard to figure out. Can you post log file?

---

### Post by meatpan on 2007-12-12
Definitely post the error messages before tying something invasive like editing a system header.  Also this problem is similar to issues people have had when the build essential package was not installed.   

Verify that you have the build-essential package:  sudo dpkg -l | grep build-essential

If the query returns nothing, or an explicitly uninstalled package state, run 'sudo apt-get install build-essential'

---


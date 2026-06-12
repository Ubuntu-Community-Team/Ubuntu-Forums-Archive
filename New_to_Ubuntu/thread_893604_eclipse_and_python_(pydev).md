---
title: "eclipse and python (pydev)"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-18
I pulled up eclipse but it was for java.  no problem I read, so I clicked a little icon in the upper right of the work bench to open perspective.  clicked other>PyDev. so now PyDev and Jave are up there in the top right but PyDev is highlighted.  Does this mean I have successfully plugged in python?
next question:  in synaptic there are two Pydevs.  the basic one installed already, and one that is GCI -native.  Do I want that?  Not sure what it is.

I have to read the directions still, but I value comments on eclipse, python, java, GCI whatevers,

---

### Post by ggaaron on 2008-08-19
Eclipse has it's own build-in extension manager (with auto updates and everything) so I would (and actually I did it this way in on my machine) install eclipse from apt and then in eclipse menu->help->update manager, add repository, add [http://pydev.sourceforge.net/updates/](http://pydev.sourceforge.net/updates/) install pydev. Now in preferences select pydev, python interpreter and set path to interpreter probably as /usr/bin/python - it will load libraries do form in centre and now you can start new project, pydev and have fun=)

---

### Post by adamogardner on 2008-08-20
sounds like a plan,  thanks for clarifying,  sorry I reply so tardily.

---

### Post by homerous on 2009-06-09
Hey 
I'm a new Pydev  user and i wanna know how to start a new project in python using eclipse i did choose file>new>project>pydev
then i stopped...
I wanna know  how to start a new module ,how to build the module and so on
if there is any link to a tutorials about it,it will be great :)

---


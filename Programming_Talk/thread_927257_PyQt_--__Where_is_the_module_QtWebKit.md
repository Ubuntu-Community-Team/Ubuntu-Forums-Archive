---
title: "PyQt --  Where is the module QtWebKit?"
date: 2008-09-22
forum: Programming Talk
---

### Post by keeler1 on 2008-09-22
I have tried to load the module PyQt4.QtWebKit to no avail.  It says that it does not exist.  Web Kit is supposed to exist now in Qt but I cant find it.

Has anyone tried it or know if it works?

---

### Post by unraveled on 2008-09-24
QtWebKit is only in Qt 4.4, Hardy is built on 4.3. Intrepid is built on 4.4 so you can either jump to that or wait another month or so.

---

### Post by keeler1 on 2008-09-25
I ended up finding a way around it.  I opened synaptic added a new third party repo which was the intrepid repo.  Grabbed the updated version of Qt4.4 and PyQt4.4.  Then I disabled the repo.

It all works great.

It was nice because I tried using it on the KDE4 version of openSuse 11 and the default PyQt package was missing webkit but the qt4 version was good enough.  So I tried 8 or so different builds of PyQt all of which supported webkit (got these from openSuse build services) but all of them had bugs in the shared object files.

I figured that the ones from the intrepid repo would have done the same but they work perfectly.

---


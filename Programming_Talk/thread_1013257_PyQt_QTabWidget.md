---
title: "PyQt QTabWidget"
date: 2008-12-16
forum: Programming Talk
---

### Post by jcas1411 on 2008-12-16
I have read the documentation and it states there exists a signal currentChanged for QTabWidget.  I have connected it using

QtCore.QObject.connect(self.ui.mainTabWidget,QtCore.SIGNAL("currentChanged()"), self.refreshTab)

I have defined refreshTab:

def refreshTab(self):
   print "here"

and its not emitting the signal when I click on any tab.

How do I detect the tab change event, am I missing something.

Using Qt 4.4.3 and installed PyQt-x11-gpl-4.4.4, Ubuntu environment. 

Thanks for any help,

---

### Post by jcas1411 on 2008-12-17
Has anyone seen this before.  I done some browsing and found in an older version there where bugs with the QTabWidget, but was fixed in the version I am running.  This is the only signal I see for the QTabWidget.. are there any others that detect click tab event?

---

### Post by digitalvectorz on 2008-12-18
A little late in response, sorry.

you might want to have a look at this post:  [http://mail.python.org/pipermail/python-list/2007-January/422958.html](http://mail.python.org/pipermail/python-list/2007-January/422958.html)

hopefully this sheds some light.

---


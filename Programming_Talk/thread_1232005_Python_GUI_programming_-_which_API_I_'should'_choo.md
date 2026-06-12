---
title: "Python GUI programming - which API I 'should' choose ?"
date: 2009-08-05
forum: Programming Talk
---

### Post by credobyte on 2009-08-05
Tkinter, WxPy, PyGTK, PyQT, etc. - I'm quite confused .. which one is the most flexible ( compatibility ) ?
Which one do you prefer and would suggest for everyone ?

---

### Post by Copernicus1234 on 2009-08-05
Probably PyGTK if you want to do desktop applications for Gnome, PyQT if you want to do them for KDE.

But the future is web applications. :) Check out Django.

---

### Post by ToyImp on 2009-08-05
GTK is by far the best. Top that with Glade and you have a WYSIWYG GUI editor/builder. 

[http://ubuntuforums.org/showthread.php?t=1231988](http://ubuntuforums.org/showthread.php?t=1231988)

check out my second post on that thread. Just posted it actually.

---

### Post by credobyte on 2009-08-05
> **Copernicus1234 said:**
> Probably PyGTK if you want to do desktop applications for Gnome, PyQT if you want to do them for KDE.

But the future is web applications. :) Check out Django.

Currently I'm *not* interested in web applications, however, will take a look at Django ( tutorials are pretty interesting ) :)

> **ToyImp said:**
> GTK is by far the best. Top that with Glade and you have a WYSIWYG GUI editor/builder. 

[http://ubuntuforums.org/showthread.php?t=1231988](http://ubuntuforums.org/showthread.php?t=1231988)

check out my second post on that thread. Just posted it actually.

Linked post made me laugh ( *wtf does this line mean* ) :D Anyway, thnx for the information/opinion :)

---

### Post by ToyImp on 2009-08-05
btw if you are looking for an IDE then I HIGHLY suggest NetBeans. Its free and supports python. Its great for debugging; which gedit does not support. :)

---

### Post by ahmatti on 2009-08-05
Have a look at this thread, its mainly about PyGTK vs PyQT [http://ubuntuforums.org/showthread.php?t=1199187](http://ubuntuforums.org/showthread.php?t=1199187), but it also discusses other toolkits. I am currently working on project with wxPython, which I think is the easiest solution to set up a nice cross platform app.

---

### Post by Viva on 2009-08-05
I recommend wxpython

---

### Post by .Maleficus. on 2009-08-05
PyQt.  Not only is it a toolkit for basic GUIs, but it also is a toolkit for multithreading, multimedia via Phonon, is integrated with WebKit, has networking functions built-in, and can work with XML and databases.  1 stop shopping.


Edit:  A [link]("http://www.qtsoftware.com/products/") with more info and available platforms.  If it can run Python it can run Qt.

---

### Post by Sockerdrickan on 2009-08-05
> **copernicus1234 said:**
>  but the future is web applications. :) check out django.
-1

---

### Post by ahmatti on 2009-08-05
> **.Maleficus. said:**
> PyQt.  Not only is it a toolkit for basic GUIs, but it also is a toolkit for multithreading, multimedia via Phonon, is integrated with WebKit, has networking functions built-in, and can work with XML and databases.  1 stop shopping.


Edit:  A [link]("http://www.qtsoftware.com/products/") with more info and available platforms.  If it can run Python it can run Qt.

Yes, QT is crossplatform and easy to set up in Linux and Windows, but the Mac setup process is pretty painful, apparently due to some errors in the installer with the newest leopard. You need to build the whole thing from source and edit the makefiles to make it work. So if you want to distribute your app to average user with a mac I wouldn't recommend PyQT.

---


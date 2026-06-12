---
title: "Portable Qt libraries?"
date: 2009-04-27
forum: Programming Talk
---

### Post by LoloftheRings on 2009-04-27
I'm developing an application in Qt, because it has to be portable and cross platform. I have to use it at school (windows xp) and at home (ubuntu). When I run the Qt app in a fresh installation, it get the error message:
./Qt: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory

Copying libQtGui.so.4 doesn't work. The easiest was is probably installing the Qt libraries, but I'm looking for a way to make it run just on every Ubuntu installation without installing anything at all. Firefox for example has the .so files in the excutable directory. How can I do this?

---

### Post by scourge on 2009-04-27
Please read the "Creating the application package" section here: [http://doc.trolltech.com/4.5/deployment-x11.html](http://doc.trolltech.com/4.5/deployment-x11.html)

---

### Post by LoloftheRings on 2009-04-28
exactly what I was looking for. Thanks!

---


---
title: "How to statically compile my project with Qt on Linux"
date: 2012-06-29
forum: Programming Talk
---

### Post by pellyhawk on 2012-06-29
I would like to statically compile my project with Qt on Ubuntu, how should I do?

I used the command:
```
./configure -static -release -qt-zlib -qt-gif -qt-libpng -qt-libmng -qt-libjpeg -nomake demos -nomake examples -qt-sql-sqlite -prefix /usr/local/Trolltech/Qt-4.7.3-static
make
make install
```

then what should I do? Thanks!

---

### Post by pellyhawk on 2012-07-01
bump

---

### Post by Dubslow on 2012-07-01
You might consider moving this to the [Compiling and Packaging]("http://ubuntuforums.org/forumdisplay.php?f=44") forum.

---


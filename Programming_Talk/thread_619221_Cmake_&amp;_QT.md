---
title: "Cmake &amp; QT"
date: 2007-11-21
forum: Programming Talk
---

### Post by Vadi on 2007-11-21
For the life of me, I cannot get cmake to compile my simple "Hello World!" program. I already got it working with qmake, so it's not *that* of a vital issue, but still, can anyone help me out?

After I do cmake . and make, it cannot do the #includes properly for whatever reason. I attached my two files, any help/explanations would be appreciated :)

(main.cpp was suffixed with .txt to comply with the uploads policy)

---

### Post by Roptaty on 2007-11-21
Hi!
The KDE4* QT* are undefined. You need to include the modules which sets them in your CMakeLists.txt file. 
Search for FindQt4 here if you are using qt4: [http://www.cmake.org/HTML/Documentation.html](http://www.cmake.org/HTML/Documentation.html)

---


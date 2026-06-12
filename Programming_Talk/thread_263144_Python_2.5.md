---
title: "Python 2.5"
date: 2006-09-22
forum: Programming Talk
---

### Post by Note360 on 2006-09-22
Hey, Python 2.5 just came out and I am wondering if I should install it. I am a Python developer/ However, I want to know if apps that rely on python 2.4 and some external libraries will brake?

---

### Post by Daverz on 2006-09-22
Shouldn't be a problem at all.  Use

make altinstall

instead of just make install.  This will install the python executable as "python2.5" and doesn't create the usual hardlink to "python".  If you just do a plain ./configure, everything will be installed under /usr/local.

---

### Post by Note360 on 2006-09-22
Ok Thanks. I installed it. I havent used it yet, but eventually I intend to learn the new changes.

---


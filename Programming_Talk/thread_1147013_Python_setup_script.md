---
title: "Python setup script"
date: 2009-05-03
forum: Programming Talk
---

### Post by matmatmat on 2009-05-03
How do you create a python script that installs a program & it's dependencies? Is it possible?

---

### Post by matmatmat on 2009-05-03
The script is for [this projects]("https://launchpad.net/pypicslideshow")

---

### Post by geirha on 2009-05-03
Using the distutils module is the common way to achieve that. [http://docs.python.org/distutils/introduction.html](http://docs.python.org/distutils/introduction.html)

---

### Post by matmatmat on 2009-05-03
Can you use this with apps

---

### Post by geirha on 2009-05-03
Yes, python apps generally has one or more modules, and a script that needs to be put in /usr/bin or /usr/local/bin. The documentation covers both.

---

### Post by salvachn on 2009-05-06
I saw an utility py2exe on Windows XP, but distutils is better.

---


---
title: "python devel headers in Ubuntu"
date: 2008-01-03
forum: Programming Talk
---

### Post by garrywillgoose on 2008-01-03
I have been writing some platform independent python software on Mac OSX, Windows and Fedora and when I tried to install one of the python extension libraries (f2py) on Ubuntu I need I got an error message 

SystemError: Non-existing /usr/include/python2.5/Python.h. Perhaps you need to install python-dev|python-devel.

I am using a ActiveState since the standard Ubuntu python is a pretty minimal install and I use ActiveState on all the other platforms. I rooted around on the web for python-devel and found 

[http://rpmfind.net/linux/rpm2html/search.php?query=python-devel](http://rpmfind.net/linux/rpm2html/search.php?query=python-devel)

but a Ubuntu install doesn't rate a mention at all here. What should I do? Can I just cp the /usr/include/python2.5 from my Fedora install or is there something special about Ubuntu I should know?

---

### Post by geirha on 2008-01-03
```
sudo aptitude install python-dev
```

---

### Post by gl4to7 on 2008-03-29
Thanks man, your answer was smack bang in the right spot

---


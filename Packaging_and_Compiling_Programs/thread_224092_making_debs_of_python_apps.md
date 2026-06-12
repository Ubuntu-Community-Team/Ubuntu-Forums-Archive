---
title: "making debs of python apps"
date: 2006-07-27
forum: Packaging and Compiling Programs
---

### Post by ssam on 2006-07-27
hello

i have a python application than can be installed using
```
./setup.py install
```

i'd like to make a .deb package of it.

i've read through the debian new maintainers guide, but it seems to assume that your program use the
```
./configure
make
make install
```
method.

does anyone know a good howto, or a program to look at as an example?

thanks

sam

---

### Post by mlind on 2006-07-28
Debian python policy should help you (Appendix B)
[http://www.debian.org/doc/packaging-manuals/python-policy/](http://www.debian.org/doc/packaging-manuals/python-policy/)

cdbs contains nice helper class for pyton that should help too
[https://perso.duckcorp.org/duck/cdbs-doc/cdbs-doc.xhtml#id2500317](https://perso.duckcorp.org/duck/cdbs-doc/cdbs-doc.xhtml#id2500317)

---

### Post by ssam on 2006-08-03
thanks

i also found this [http://maemo.org/platform/docs/pymaemo/python_maemo_howto.html](http://maemo.org/platform/docs/pymaemo/python_maemo_howto.html) which describes making deb packages to nokia 770s. they make a Makefile that runs the setup.py script.

---

### Post by ssam on 2006-08-05
it works (works for me on 2 ubuntu machines).

[http://sourceforge.net/project/showfiles.php?group_id=172470](http://sourceforge.net/project/showfiles.php?group_id=172470)

---


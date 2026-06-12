---
title: "multiple python versions coexist on Ubuntu?"
date: 2008-06-13
forum: Programming Talk
---

### Post by unbuntu on 2008-06-13
I'm trying to install Zope2.5 and Plone3.1 on Ubuntu.  They both run only on Python 2.4 but Hardy comes with Python 2.5

I noticed Python 2.4 is in the repository.  However, I don't want to mess up with the current Python 2.5 installation.  I'm wondering how can multiple versions of python coexist under Ubuntu?

Thanks,

---

### Post by shadylookin on 2008-06-14
I"m pretty sure it's backwards compatible so running it with python 2.5 should be fine.

v3 is going to the the version that breaks backwards compatibility

---

### Post by geirha on 2008-06-14
python2.4 and python2.5 will happily coexist. Python2.5 puts its libraries in /usr/lib/python2.5 while python2.4 puts them in /usr/lib/python2.4 and so forth. /usr/bin/python will typically be a symlink to the latest version of python (/usr/bin/python2.5), and you can specifically use version 2.4 by running /usr/bin/python2.4.

---


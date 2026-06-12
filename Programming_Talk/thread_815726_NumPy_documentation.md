---
title: "NumPy documentation"
date: 2008-06-01
forum: Programming Talk
---

### Post by Stochastics on 2008-06-01
Hi,

I've just installed Python/SciPy/NumPy from the repositories and i want to know where is located all the documentations for these. Anyone can help ?

Stochastics.

---

### Post by geirha on 2008-06-02
Numpy has a seperate -doc package; [python-numpy-doc](apt://python-numpy-doc), which will install some docs in /usr/share/doc/python-numpy-doc/

Scipy don't seem to have a seperate -doc package, but the module's internal doc seems to be good ```
>>> help('scipy')
```

---


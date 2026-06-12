---
title: "matplotlib, numpy on dapper?"
date: 2006-12-30
forum: Programming Talk
---

### Post by fadder on 2006-12-30
I'm trying to use matplotlib+numpy on a dapper installation. I had to download numpy by hand, and it installed fine. But when I edit my matplotlibrc file to use numpy, ipython -pylab gives:

/usr/lib/python2.4/site-packages/matplotlib/__init__.py:719: UserWarning: Bad val "numpy" on line #33
        "numerix      : numpy   # Numeric or numarray"
        in file "/home/fadder/matplotlibrc"
        Numerix must be Numeric or numarray


How can I tell my python/ipython/matplotlib distribution to use the new numpy? (If I just type python, then I can import numpy fine, but not matplotlib for the same reason as given above.
I prefer to avoid upgrading to edgy just to fix this, so help appreciated. Thanks.

---

### Post by dwblas on 2007-01-01
The Ubuntu package is called python-numpy.  Try installing it with Synaptic or whatever.

---

### Post by fadder on 2007-01-03
I tried that, but for some reason it didn't work (does work fine on my Edgy computer,  but not om my Dapper one). Now I have got things working by using the repository from Andrew Straw: [http://debs.astraw.com/dapper/](http://debs.astraw.com/dapper/)

I had to uninstall some of the standard dapper stuff and then reinstall numpy and matplotlib.
Works great now.

---


---
title: "(Python) ImportError: No module named RandomArray"
date: 2017-02-14
forum: New to Ubuntu
---

### Post by abulafia89 on 2017-02-14
Dears,

I've Python 2.7.12 version installed, with  visual, numpy, matplotlib and scipy  correctly installed.

**The following code:**

[I]import visual as vi
c = vi.cone(radius=1.0e-10)
c.visible = 0
import numpy
import pylab
import RandomArray [/I]
[B]
Gives me the following error:[/B]

[I]ImportError: No module named RandomArray

[/I]Thank you in advance!!!

---

### Post by steeldriver on 2017-02-14
Hello and welcome to the forums

As far as I can tell, RandomArray is an ancient (pre-numpy) 'Numeric' module that was shuffled off into an oldnumeric package and finally dropped from numpy 1.9


[https://docs.scipy.org/doc/numpy/reference/routines.oldnumeric.html](https://docs.scipy.org/doc/numpy/reference/routines.oldnumeric.html)
[http://www.numpy.org/old_array_packages.html](http://www.numpy.org/old_array_packages.html)

---


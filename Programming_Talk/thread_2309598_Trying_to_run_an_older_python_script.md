---
title: "Trying to run an older python script"
date: 2016-01-11
forum: Programming Talk
---

### Post by Chris_Laskaris on 2016-01-11
I am trying to run an older python script, which can be found here:

[ftp://ftp.mcs.anl.gov/pub/People/mickelso/slarti1.5/MakeCouplerRestart.py](ftp://ftp.mcs.anl.gov/pub/People/mickelso/slarti1.5/MakeCouplerRestart.py)

It begins with:  *import MV,struct,Numeric,string*

First, I got the error message *ImportError: No module named MV*. I am told that the program can still be used without problems without MV, so I removed it. Numeric is no longer in use and has been replaced with numpy, so I installed the python-numpy package (and the python-scipy package for good measure) and replaced all instances of Numeric in the script with numpy.

Now I am getting the error:

```
Traceback (most recent call last):
  File "MakeCouplerRestart.py", line 90, in <module>
    oro = numpy.zeros((uwlat,uwlon),numpy.Float32)
AttributeError: 'module' object has no attribute 'Float32'
```

This seems to be the problematic part of the code:

```
oro = numpy.zeros((uwlat,uwlon),numpy.Float32)
oro.savespace(1)
getCouplerData('mask.128x128',oro)
ioro = oro.astype(numpy.Int) #Convert to integer
ioro.savespace(1)
oioro = ioro.copy()
```

I am not good at python, so if anyone could point me towards where the error lies, I'd be very grateful. Thank you.

---

### Post by Vaphell on 2016-01-12
try lowercasing the type name.
```

>>> import numpy
>>> numpy.Float32
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'Float32'
>>> numpy.float32
<type 'numpy.float32'>
```

---


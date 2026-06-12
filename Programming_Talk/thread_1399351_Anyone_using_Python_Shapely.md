---
title: "Anyone using Python Shapely?"
date: 2010-02-05
forum: Programming Talk
---

### Post by A_Fiachra on 2010-02-05
I have several installs and on two of them I get errors with the libgeos shared object.

One tells me:

```

python -c 'from shapely import wkt'
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/local/lib/python2.6/dist-packages/Shapely-1.2a1-py2.6.egg/shapely/wkt.py", line 7, in <module>
    from shapely.geos import lgeos, allocated_c_char_p, ReadingError
  File "/usr/local/lib/python2.6/dist-packages/Shapely-1.2a1-py2.6.egg/shapely/geos.py", line 65, in <module>
    _lgeos = CDLL('libgeos_c.so')
  File "/usr/local/lib/python2.6/dist-packages/ctypes-1.0.2-py2.6-linux-i686.egg/ctypes/__init__.py", line 340, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: libgeos-3.2.0.so: cannot open shared object file: No such file or directory

```


But :

```

$ ls -l /usr/lib/libgeos*
lrwxrwxrwx 1 root root 27 2010-02-05 13:19 /usr/lib/libgeos_c.so -> /usr/local/lib/libgeos_c.so

```

wtf??

---


---
title: "Python-matplotlib RuntimeError: '/home/user/' is not a writable dir;"
date: 2009-03-30
forum: Programming Talk
---

### Post by ppeetteerr on 2009-03-30
I'm trying to run matplotlib in python.  When I run 
```

import matplotlib 

```

I get 
```

>>> import matplotlib
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 709, in <module>
    rcParams = rc_params()
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 627, in rc_params
    fname = matplotlib_fname()
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 565, in matplotlib_fname
    fname = os.path.join(get_configdir(), 'matplotlibrc')
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 240, in wrapper
    ret = func(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 436, in _get_configdir
    raise RuntimeError("'%s' is not a writable dir; you must set %s/.matplotlib to be a writable dir.  You can also set environment variable MPLCONFIGDIR to any writable directory where you want matplotlib data stored "% (h, h))
RuntimeError: '/home/peter' is not a writable dir; you must set /home/peter/.matplotlib to be a writable dir.  You can also set environment variable MPLCONFIGDIR to any writable directory where you want matplotlib data stored 
>>> import matplotlib
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 709, in <module>
    rcParams = rc_params()
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 627, in rc_params
    fname = matplotlib_fname()
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 565, in matplotlib_fname
    fname = os.path.join(get_configdir(), 'matplotlibrc')
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 240, in wrapper
    ret = func(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 436, in _get_configdir
    raise RuntimeError("'%s' is not a writable dir; you must set %s/.matplotlib to be a writable dir.  You can also set environment variable MPLCONFIGDIR to any writable directory where you want matplotlib data stored "% (h, h))
RuntimeError: '/home/peter' is not a writable dir; you must set /home/peter/.matplotlib to be a writable dir.  You can also set environment variable MPLCONFIGDIR to any writable directory where you want matplotlib data stored 

```

---

### Post by unutbu on 2009-03-30
Please post```

ls -ld /home/peter
ls -ld /home/peter/.matplotlib
```

---


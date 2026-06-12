---
title: "Simple python query"
date: 2011-08-06
forum: Programming Talk
---

### Post by bouncingwilf on 2011-08-06
Sorry to have to post this but it has had me scratching my head for an hour or two, no obvious answers using search and I though a wiser head could possibly save me some frustration. I'm trying python for the first time and I want to use the quikgrid add on functions. Downloaded and compiled quikgrid, the library all ok but when I try the capy_test.py program, it complains that it can't find the shared library. error is:

```
Traceback (most recent call last):
  File "capi_test.py", line 1, in <module>
    from capi import SurfaceGrid
  File "/home/wilf/quikgrid-read-only/python/quikgrid/capi.py", line 23, in <module>
    raise ImportError("Cannot find libquikgrid shared object.")
ImportError: Cannot find libquikgrid shared object.

```

But -  libquikgrid.so is available in both the current directory and /usr/local/lib/python2.6/dist-packages
which is listed as in the path by python

```
wilf@wilf-desktop:~/quikgrid-read-only/python/quikgrid$ python -c "import sys; print sys.path"
['', '/usr/local/lib/python2.6/dist-packages/quikgrid-0.5.3a-py2.6.egg', '/usr/lib/python2.6', '/usr/lib/python2.6/plat-linux2', '/usr/lib/python2.6/lib-tk', '/usr/lib/python2.6/lib-old', '/usr/lib/python2.6/lib-dynload', '/usr/lib/python2.6/dist-packages', '/usr/lib/python2.6/dist-packages/PIL', '/usr/lib/python2.6/dist-packages/gst-0.10', '/usr/lib/pymodules/python2.6', '/usr/lib/python2.6/dist-packages/gtk-2.0', '/usr/lib/pymodules/python2.6/gtk-2.0', '/usr/local/lib/python2.6/dist-packages']

```

I've checked permissions and ensured they're readable so possibly the error comes from the capi_test routine - being a total python noob I'd have no way of knowing (yet)

relevant capi_test code is 
```
lqg = None 
for ext in ['so','dylib','so']: 
    try: 
        lqg = CDLL( os.path.join(os.path.basename(__file__), 'libquikgrid.' + ext ) ) 
    except OSError,e: 
        pass 
 
if not lqg: 
    raise ImportError("Cannot find libquikgrid shared object.") 

```
  all a bit of a mystery to me at this stage as it looks as if it should work, I would be grateful if someone could give me a pointer or two

Bouncingwilf

---

### Post by StephenF on 2011-08-06
The python path is for loading python modules which I assume this is not on account of the .so extension.

After installing the library check that it is in a place listed in /etc/ld.so.conf or add an entry, then run ldconfig as root.

---

### Post by bouncingwilf on 2011-08-06
Well I've added an entry in /etc/ld.so.conf.d, run ldconfig and also added a copy to /usr/lib/python2.6 but still the same error! 

any further ideas please?

Bouncingwilf

---

### Post by bouncingwilf on 2011-08-07
Well I've sort of solved it by re-writing the python code to search the current directory ( I think - groping about in the dark here!) 

The relevant code is

```
try:
    lqg = CDLL( './libquikgrid.so' )
except OSError,e:
    lqg = CDLL(find_library('quikgrid'))

```

This now works. Hopefully as time goes on I'll understand what I deleted!

Bouncingwilf

---


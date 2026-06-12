---
title: "error starting Ipython on hoary"
date: 2005-02-10
forum: Programming Talk
---

### Post by blixtra on 2005-02-10
I'm getting this error when I start ipyhon on hoary with all updates.

```
Traceback (most recent call last):
  File "/usr/bin/ipython", line 26, in ?
    import IPython
  File "/usr/lib/python2.4/site-packages/IPython/__init__.py", line 52, in ?
    __import__(name,glob,loc,[])
  File "/usr/lib/python2.4/site-packages/IPython/Shell.py", line 30, in ?
    from IPython.iplib import InteractiveShell
  File "/usr/lib/python2.4/site-packages/IPython/iplib.py", line 54, in ?
    from IPython.Magic import Magic,magic2python,shlex_split
  File "/usr/lib/python2.4/site-packages/IPython/Magic.py", line 24, in ?
    import os,sys,inspect,pydoc,re,tempfile,profile,pstats,shlex,pdb,bdb
[COLOR=Red]ImportError: No module named profile[/COLOR]

```

From what I googled profile is a standard module.

Is anyone else getting this and does anyone know a fix?

Chris

---

### Post by GilGalad on 2005-02-10
I got the same error and this is how I fixed it. It seems that the profiler module has been taken out of python2.4 and packaged separately. You need the python2.4-profiler
package and I could not find a compiled version so:

apt-get source python2.4-profiler
cd python-profiler-2/
fakeroot dpkg-buildpackage
sudo dpkg -i ../python-profiler_2.4-2ubuntu1_all.deb ../python2.4-profiler_2.4-2ubuntu1_all.deb

---

### Post by blixtra on 2005-02-10
While I was trying your fix and getting package not found errors, I refreshed synaptic and under "new in repository" there was python2.4-profiler and everything if fine.

Thanks anyways.

Chris

---


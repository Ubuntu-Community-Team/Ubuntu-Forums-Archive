---
title: "ipython does not start"
date: 2011-09-10
forum: Programming Talk
---

### Post by random3f on 2011-09-10
Dear All,
I have several problems with ipython.
I would like to use matplotlib and Mayavi2 but 
after the installation of numpy and all these libraries
i tried to run ipython and I got:
> $ ipython 
Traceback (most recent call last):
  File "/usr/local/bin/ipython", line 9, in <module>
    load_entry_point('ipython==0.10.1', 'console_scripts', 'ipython')()
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 305, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2243, in load_entry_point
    raise ImportError("Entry point %r not found" % ((group,name),))
ImportError: Entry point ('console_scripts', 'ipython') not found

Here it is, I have no idea what to do to solve this problem.
Could you help me?

I'm using Ubuntu 11.04 64bit.
Can python 2.6 create problems? It is already installed and I don't know if I can remove it.

Thanks!!

---

### Post by minrk on 2011-09-10
the script is associated with a particular version of IPython (this is what setuptools always does), but that version is probably not installed.  Reinstalling IPython should do the trick, but you can also check more thoroughly, with:

In regular Python:

```
>>> import IPython
>>> print IPython.__version__
>>> print IPython.__file__

```

to see where/what version IPython is.

and check if you might have more than one IPython startup script, with:

```
$> which -a ipython
```

---

### Post by random3f on 2011-09-10
Yes, You are right!
I have ```
which -a ipython
/usr/local/bin/ipython
/usr/bin/ipython

``` 
Only the second one works. Now I should find a way to uninstall the first one.

The other tests that you suggested give:
```
import IPython
print IPython.__version__
0.10.1
print IPython.__file__
/usr/lib/python2.7/dist-packages/IPython/__init__.pyc

```

I tried to re-install several times but nothing changed. Actually synaptic  says that the only file it installed is the second one (the right one) so I guess I messed up everything using also easy_install. 
Thank you very much! Now I can work!!

How can I repair the double installation? 

In fact, something is still wrong. The first time I wrote on ipython "help" then "modules" it writes
```
/usr/lib/python2.7/dist-packages/zope/__init__.py:3: UserWarning: Module test was already imported from /usr/lib/python2.7/test/__init__.pyc, but /usr/lib/pymodules/python2.7 is being added to sys.path
  import pkg_resources
(18398)/kdeui (Wallet): The kwalletd service has been disabled 
(18398)/kdeui (Wallet): The kwalletd service has been disabled 
(18398)/kdeui (Wallet): The kwalletd service has been disabled 
(18398)/kdeui (Wallet): The kwalletd service has been disabled 
(18398)/kdeui (Wallet): The kwalletd service has been disabled 
(18398)/kdeui (Wallet): The kwalletd service has been disabled 
/usr/lib/python2.7/dist-packages/twisted/words/im/__init__.py:8: UserWarning: twisted.im will be undergoing a rewrite at some point in the future.
  warnings.warn("twisted.im will be undergoing a rewrite at some point in the future.")
No handlers could be found for logger "OpenGL.Tk"
SHARED_DATA_DIR: /usr/share/glipper
Binding shortcut <Ctrl><Alt>c to popup glipper

** (ipython:18398): WARNING **: Binding '<Ctrl><Alt>c' failed!
/usr/lib/pymodules/python2.7/matplotlib/__init__.py:835: UserWarning:  This call to matplotlib.use() has no effect
because the the backend has already been chosen;
matplotlib.use() must be called *before* pylab, matplotlib.pyplot,
or matplotlib.backends is imported for the first time.

  if warn: warnings.warn(_use_error_msg)

```  and then it write the list of modules. Is it related to my mistake?

Thank you again for your help and for any other suggestion!

---


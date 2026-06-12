---
title: "Can't get wxPython to work with Python 2.6.4"
date: 2009-11-17
forum: Programming Talk
---

### Post by rob86 on 2009-11-17
I have wxPython gtk-2.8and 2.6 installed (why both? Don't ask me, ask Jaunty!) and python 2.6.2 also installed, all three with Synaptic.

I needed Python 2.6.4 so I compiled it myself with check install, and now when I try to import 'wx' in this version, it says module not found.

Any idea why? Do I need to manually compile  wxpython (not with synaptic) and then re-compile python? 

```
Python 2.6.4 (r264:75706, Nov 17 2009, 18:46:54) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import wx
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named wx


```
```
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import wx
>>> wx
<module 'wx' from '/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/__init__.pyc'>
>>> 
ImportError: No module named wx

```I just noticed that it's using wx-2.6 instead of 2.8, strange indeed!

Can someone help me get Python2.6.4 and wxPython 2.8 working -- together? Thanks.

---

### Post by casevh on 2009-11-18
I'm guessing you installed Python 2.6.4 to a different location such as /usr/local. The search path for your version of Python doesn't know where wx is located. Try setting the environment variable PYTHONPATH to "/usr/lib/python2.6/dist-packages". For a permanent fix, you could edit your site.py file.

HTH,

casevh

---

### Post by rob86 on 2009-11-18
Thanks for the reply. I thought you were on to something when I checked the pythonpath of both versions and they differed.

```
Python 2.6.4:
1 /usr/local/lib/python26.zip
2 /usr/local/lib/python2.6
3 /usr/local/lib/python2.6/plat-linux2
4 /usr/local/lib/python2.6/lib-tk
5 /usr/local/lib/python2.6/lib-old
6 /usr/local/lib/python2.6/lib-dynload
7 /usr/local/lib/python2.6/site-packages
``````
Python 2.6.2:
0 /usr/local/lib/python2.6/dist-packages
1 /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode
2 /usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode
3 /var/lib/python-support/python2.6/gtk-2.0
4 /usr/lib/python2.6/dist-packages/gtk-2.0
5 /var/lib/python-support/python2.6
6 /usr/lib/python2.6/dist-packages/gst-0.10
7 /usr/lib/python2.6/dist-packages/PIL
8 /usr/lib/python2.6/dist-packages/Numeric
9 /usr/lib/python2.6/dist-packages
10 /usr/lib/python2.6/lib-dynload
11 /usr/lib/python2.6/lib-old
12 /usr/lib/python2.6/lib-tk
13 /usr/lib/python2.6/plat-linux2
14 /usr/lib/python2.6
```I first tried
```
>>> sys.path.append("/usr/lib/python2.6/dist-packages")
>>> import wx
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named wx

```As you can see, didn't work. So I thought, why not just copy the entire path list from 2.6.2 to 2.6.4? I tried that....

```
>>> import wx
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
ImportError: /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core_.so: undefined symbol: PyUnicodeUCS4_FromWideChar



```No luck with that either, unfortunately :(

---

### Post by casevh on 2009-11-18
We're getting further. By default, Python uses UCS2 for Unicode but Ubuntu uses UCS4. Try re-compiling Python 2.6.4 with --enable-unicode=ucs4.

casevh

---

### Post by rob86 on 2009-11-19
Doing that helped a little, but looks there's another error now.

```
>>> import wx
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in <module>
    from wx._core import *
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13446, in <module>
    import locale
  File "/usr/lib/python2.6/locale.py", line 15, in <module>
    import functools
  File "/usr/lib/python2.6/functools.py", line 10, in <module>
    from _functools import partial, reduce
ImportError: No module named _functools
>>> 

```

Certainly not the easiest thing in the world to install!

---

### Post by casevh on 2009-11-19
The following works for me (on Karmic, anyway)

```
PYTHONPATH="/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode" py26
```

Does import "import locale" work in your 2.6.4 version?

casevh

---

### Post by rob86 on 2009-11-19
I think doing that worked, I tried a few things that didn't work previously and now they do! Thanks! How can I make this permanent? I know you said something about site.py, but I don't know what you meant by that.

Since you're on a roll, I have another question related to the upgrade.

I made an app in Tkinter, and when I run it with python 2.6.2, it seems to fit the way my desktop looks (Same colours, same fonts, same scroll bar, etc..) but when I run it with 2.6.4, it looks, well, old fashioned. Everything's grey by default, the scrollbars fatter, entry forms are thinner. Any idea why there's a difference?

---

### Post by casevh on 2009-11-19
Here is a link to the docs describing how to modify the search path:
[HTML]http://docs.python.org/install/index.html#modifying-python-s-search-path[/HTML]

I created a file in /usr/local/lib/python2.6/site-packages called "stdlibs.py" with the contents:
```
/usr/lib/python2.6/dist-packages
/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode

```

I was able to access wx and PIL from the default installation. Add other directories as needed.

Regarding Tk, I don't really use it. I tried a quick demo and both installations looked the same. I have tk8.4-dev installed. What version do you have installed?

casevh

---


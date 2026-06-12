---
title: "Python GTK"
date: 2011-04-16
forum: Programming Talk
---

### Post by Mosabama on 2011-04-16
I want to start learning GUI with python.

I have seen examples online on using python with GTK, and then they say that pygtk to be used if you wanna make gtk applications with python.

I tried an example by importing GTK only not PyGTK and it worked.

so whats the difference then? if GTK alone works why do I have to use pygtk?

Thanks in advance

---

### Post by simeon87 on 2011-04-16
If you do 'import gtk' then you are using PyGTK. You can also do 'import pygtk' which provides additional functionality, I'm not entirely sure because I only need it to check the version number of PyGTK. It's very common to do:

```
import pygtk
pygtk.require('2.0')
```

to demand that a minimum version of PyGTK is installed.

PyGTK is a so-called binding for GTK, which is actually written in C. So you'll be using the module gtk the most as it directly corresponds to the classes and code in C.

---

### Post by Mosabama on 2011-04-16
thanks for the reply..
the tutorial I am following imports both GTK and PYGTK... when I run the program with both imported it runs when I remove pygtk .. also runs the same!!!

is importing pygtk only to make sure about the version? cause I cant see it anywhere else.. there no such pygtk.window() line for example ... its never used !!

---

### Post by simeon87 on 2011-04-16
> **Mosabama said:**
> thanks for the reply..
the tutorial I am following imports both GTK and PYGTK... when I run the program with both imported it runs when I remove pygtk .. also runs the same!!!

is importing pygtk only to make sure about the version? cause I cant see it anywhere else.. there no such pygtk.window() line for example ... its never used !!

It's mainly for checking the version number I think:

```
>>> import pygtk
>>> dir (pygtk)
['__all__', '__builtins__', '__doc__', '__file__', '__name__', '__package__', '_get_available_versions', '_our_dir', '_pygtk_2_0_dir', '_pygtk_dir_pat', '_pygtk_required_version', 'fnmatch', 'glob', 'os', 'require', 'require20', 'sys']
```

I haven't seen it in use for any other purpose either.

---

### Post by Mosabama on 2011-04-16
that makes sense I guess.

Thanks

---


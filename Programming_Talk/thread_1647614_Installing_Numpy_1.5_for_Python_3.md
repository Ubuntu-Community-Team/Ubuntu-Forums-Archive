---
title: "Installing Numpy 1.5 for Python 3"
date: 2010-12-17
forum: Programming Talk
---

### Post by imple on 2010-12-17
Hi,
I'm trying to install Numpy for Python 3 and am hoping that someone here can give me a hand. I've downloaded the source, extracted it and run:

```
sudo python3 setup.py build
sudo python3 setup.py install
```

Now, when I run python3 and then import numpy from the interpreter, I get the error:

```

Python 3.1.2 (release31-maint, Sep 17 2010, 20:34:23) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy
Traceback (most recent call last):
  File "numpy/__init__.py", line 122, in <module>
    from numpy.__config__ import show as show_config
ImportError: No module named __config__

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "numpy/__init__.py", line 127, in <module>
    raise ImportError(msg)
ImportError: Error importing numpy: you should not try to import numpy from
        its source directory; please exit the numpy source tree, and relaunch
        your python intepreter from there.

```

I can't seem to make much sense of this. Thanks!

---

### Post by Tlingit on 2011-01-06
I am actually trying to figure this out as well, did you even get numpy installed and what version of ubuntu are you using?

Did you get this installed?

Here is my thread.



[http://ubuntuforums.org/showthread.php?t=1660809]("http://ubuntuforums.org/showthread.php?t=1660809")

---

### Post by Vox754 on 2011-01-06
> **Tlingit said:**
> I am actually trying to figure this out as well, did you even get numpy installed and what version of ubuntu are you using?

Did you get this installed?

Here is my thread.



[http://ubuntuforums.org/showthread.php?t=1660809]("http://ubuntuforums.org/showthread.php?t=1660809")

As you can see, some very useful libraries have not yet been ported to Python 3. Therefore, the only sensible solution at this point is to avoid Python 3, and stick to the good ole Python 2.

The Numpy FAQ mentions that [they expected a first release of Numpy for Python 3 by mid 2010.](http://new.scipy.org/faq.html#python-version-support) It seems they were too optimistic about that. Perhaps wait another year.

---

### Post by takowl on 2011-01-14
> **Vox754 said:**
> The Numpy FAQ mentions that [they expected a first release of Numpy for Python 3 by mid 2010.](http://new.scipy.org/faq.html#python-version-support) It seems they were too optimistic about that. Perhaps wait another year.

Nope, in fact they were about right. [Numpy 1.5]("http://mail.scipy.org/pipermail/numpy-discussion/2010-August/052522.html") was released at the end of August with Python 3 support.

If you look, the error message itself gives you the answer: 

> you should not try to import numpy from its source directory; please exit the numpy source tree, and relaunch your python intepreter from there.

So just cd back to your home directory (or any other folder), then start Python 3 and try importing it. Works for me! (Ubuntu 10.10)

Also, you might want to read the instructions in numpy's INSTALL.txt, where they suggest installing some libatlas packages before building numpy.

---

### Post by takowl on 2011-01-14
(duplicate post removed)

---

### Post by Vox754 on 2011-01-14
> **takowl said:**
> Nope, in fact they were about right. [Numpy 1.5]("http://mail.scipy.org/pipermail/numpy-discussion/2010-August/052522.html") was released at the end of August with Python 3 support.

If you look, the error message itself gives you the answer: 



So just cd back to your home directory (or any other folder), then start Python 3 and try importing it. Works for me! (Ubuntu 10.10)

Also, you might want to read the instructions in numpy's INSTALL.txt, where they suggest installing some libatlas packages before building numpy.

Oh, that's great news. Thanks for the update.

I guess this means more and more packages are finally getting into Python 3.

Still, my advice for beginners, who aren't experienced enough, is stick to Python 2 while you learn. Once you know what works and what doesn't, move to Python 3 if you can deal with it.

---

### Post by takowl on 2011-02-01
> **Vox754 said:**
> Still, my advice for beginners, who aren't experienced enough, is stick to Python 2 while you learn. Once you know what works and what doesn't, move to Python 3 if you can deal with it.

I reckon it's reaching a turning point. I'd say: if you want to get up and running with a serious project (especially a website) quickly, go with Python 2, because the libraries and information are out there. If you want to learn more gradually, and just write small programs for yourself, Python 3 is probably a good bet. Switching later "if you can deal with it" seems the wrong way round - Python 3 is the simpler one in a few ways (no xrange, iteritems, and so on), and switching back to Python 2 would probably require more understanding.

Library support is slowly picking up. I'm trying to catalogue the status of Python 3 support in a spreadsheet - feel free to add information: [https://spreadsheets.google.com/ccc?key=0AqIElKUDQl8tdC1lR29XZFlxZUxOU1VlZ1JRQ3ZRanc&hl=en_GB](https://spreadsheets.google.com/ccc?key=0AqIElKUDQl8tdC1lR29XZFlxZUxOU1VlZ1JRQ3ZRanc&hl=en_GB)

---


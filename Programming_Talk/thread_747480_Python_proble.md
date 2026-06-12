---
title: "Python proble"
date: 2008-04-06
forum: Programming Talk
---

### Post by urosh2 on 2008-04-06
Hi there.

I have one problem with python.

When i run comand for example in SPE or ERIC the code works.
```

import wx
import math
import pylab
import matplotlib

print('Hello world')

```
I get output 
Hello world
But when i run this code in console i get:
```

uros@uros-laptop:~/Documents/Programiranje/sara$ python jjjj.py 
Traceback (most recent call last):
  File "jjjj.py", line 3, in <module>
    import pylab
  File "/usr/lib/python2.5/site-packages/pylab.py", line 1, in <module>
    from matplotlib.pylab import *
  File "/usr/lib/python2.5/site-packages/matplotlib/pylab.py", line 199, in <module>
    import cm
  File "/usr/lib/python2.5/site-packages/matplotlib/cm.py", line 5, in <module>
    import colors
  File "/usr/lib/python2.5/site-packages/matplotlib/colors.py", line 38, in <module>
    from numerix import array, arange, take, put, Float, Int, putmask, \
  File "/usr/lib/python2.5/site-packages/matplotlib/numerix/__init__.py", line 82, in <module>
    import numpy
  File "/usr/lib/python2.5/site-packages/numpy/__init__.py", line 43, in <module>
    import linalg
  File "/usr/lib/python2.5/site-packages/numpy/linalg/__init__.py", line 4, in <module>
    from linalg import *
  File "/usr/lib/python2.5/site-packages/numpy/linalg/linalg.py", line 25, in <module>
    from numpy.linalg import lapack_lite
ImportError: /usr/lib/atlas/liblapack.so.3: undefined symbol: ATL_chemv


```
I tried with python2.5 and python2.4
Thanks anyone who can help me.

:(

---

### Post by Glaxed on 2008-04-06
It seems that a symbol object in lapack_lite is not recognized by Python.
This is not your fault, at least I dont think it is.
Lots of modules are being imported by modules you imported, so Python may just be getting confused, thought that probabl doesnt explain why it worked in an IDE before.
I don't know what the problem is :D, but I have a (bad) temporary fix.
```

try:
    import wx
    import math
    import pylab
    import matplotlib
except ImportError:
    pass

print 'Hello world'

```
only thing i can think of.

Edit>>> Does anyone know if SPE or Eric uses special python tags when executing scripts? Perhaps you should execute that with those tags (ie -a, -b etc.)

---

### Post by urosh2 on 2008-04-06
Thanks for replay. :KS
But this solution doesn't work for me, because i need to import that libraries. In SPE works but in console no. This isn't a full program i just write an example, but the point is the same.

Maybe anyone else sees solution.

Thanks.

---

### Post by xelapond on 2008-04-07
I don't have a solution, but one of my programs I wrote on the console will not run in ERIC because of import errors.  I imported PyQt4, which is seemed to have a problem with.  I think ERIC does use some different importing system though.

Alex

---

### Post by Glaxed on 2008-04-08
My belief is that they all use the same importing system, or else they wouldn't be Python IDEs, no?
Eric is based of Scintilla, but not GTK. Mebbe Qt has issues launching other qt programs..
I know from experience that using GTK and Tk in the same python file can cause an ugly X error.
I haven't used ERIC or SPE for a while. Both have good features, but dont integrate well with my other programs.
Give Geany a shot, it's an **amazing** IDE.
Very lightweight, and tons of features - see if your Python will run under Geany.

I have another idea; try
```

$ chmod +x yourpythonscript.py
$ ./yourpythonscript.py
#or
$ python yourpythonscript.py

```

If you are determined, peek into the SPE.py file and find clues as to how it actually executes scripts. You'd need to be able to read past Wx and obfuscated stuff, though.

---

### Post by urosh2 on 2008-04-08
Still. Doesnt work. The same errors.
on 
./jjjj.py
```

uros@uros-laptop:~/Documents/Programiranje/sara$ ./jjjj.py 
./jjjj.py: line 1: import: command not found
./jjjj.py: line 2: import: command not found
./jjjj.py: line 3: import: command not found
./jjjj.py: line 4: import: command not found
./jjjj.py: line 6: syntax error near unexpected token `'Hello world''
./jjjj.py: line 6: `print('Hello world')'
uros@uros-laptop:~/Documents/Programiranje/sara$ 


```

---

### Post by smartbei on 2008-04-08
Well, the reason this doesn't work is becuase you forgot to stick a shebang in the first line of the python file.
Put:
```

#!/usr/bin/python

```
as the first line of the file.

---

### Post by urosh2 on 2008-04-08
Thanks

It still has errors in terminal, bun when i run it in Nautilus, it works.

---

### Post by Glaxed on 2008-04-10
You need to run in the terminal as a python script.
Right now, it is executing as a shell script; the eqivalent of;
```
sh jjjj.py
```
instead of
```
python jjjj.py
```. Try the latter.
And please remember to put
> #!/usr/bin/env python
at the top of every Python file :).

---

### Post by adybbroe on 2008-10-02
> **urosh2 said:**
> Hi there.

I have one problem with python.

When i run comand for example in SPE or ERIC the code works.
```

import wx
import math
import pylab
import matplotlib

print('Hello world')

```
I get output 
Hello world
But when i run this code in console i get:
```

uros@uros-laptop:~/Documents/Programiranje/sara$ python jjjj.py 
Traceback (most recent call last):
  File "jjjj.py", line 3, in <module>
    import pylab
  File "/usr/lib/python2.5/site-packages/pylab.py", line 1, in <module>
    from matplotlib.pylab import *
  File "/usr/lib/python2.5/site-packages/matplotlib/pylab.py", line 199, in <module>
    import cm
  File "/usr/lib/python2.5/site-packages/matplotlib/cm.py", line 5, in <module>
    import colors
  File "/usr/lib/python2.5/site-packages/matplotlib/colors.py", line 38, in <module>
    from numerix import array, arange, take, put, Float, Int, putmask, \
  File "/usr/lib/python2.5/site-packages/matplotlib/numerix/__init__.py", line 82, in <module>
    import numpy
  File "/usr/lib/python2.5/site-packages/numpy/__init__.py", line 43, in <module>
    import linalg
  File "/usr/lib/python2.5/site-packages/numpy/linalg/__init__.py", line 4, in <module>
    from linalg import *
  File "/usr/lib/python2.5/site-packages/numpy/linalg/linalg.py", line 25, in <module>
    from numpy.linalg import lapack_lite
ImportError: /usr/lib/atlas/liblapack.so.3: undefined symbol: ATL_chemv


```
I tried with python2.5 and python2.4
Thanks anyone who can help me.

:(

Hi,

I had the same error here on my Gutsy Gibbon installation.
Apparently the python-numeric-ext package is broken:
>>> import lapack_lite
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: /usr/lib/atlas/liblapack.so.3: undefined symbol: ATL_chemv
>>> 

I downloaded the Numeric-24.2 source and build it myself:
> python setup.py build
> python setup.py install --prefix=/local_disk/opt/Numeric-24_2


I moved the original package just in case and copied my newly build one to the site-packages dir, and everything seems to work now.

Try:
python -c "import lapack_lite"

...now, hopefully it doesn't complain anymore.

Good luck.
Adam

---


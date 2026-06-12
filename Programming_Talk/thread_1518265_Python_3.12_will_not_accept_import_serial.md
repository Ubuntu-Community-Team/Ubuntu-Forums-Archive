---
title: "Python 3.12 will not accept import serial"
date: 2010-06-26
forum: Programming Talk
---

### Post by Spiritof76 on 2010-06-26
I am trying to import a Python program which I wrote in 2.61 to 3.12.  I get an error when I attempt to "import serial"
```
>>> import serial
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    import serial
ImportError: No module named serial
```
Did 3.0 do away with serial communications or is this a bug?  Is there a way I can get serial communications to work in Python 3.x? 

TIA for any help anyone can give me.  I

---

### Post by DanielWaterworth on 2010-06-26
serial isn't in the standard library, you need to get the python3 version.

---

### Post by Spiritof76 on 2010-06-26
Where would I find this python3 version and does it come with instructions on how to install it in Ubuntu?
curses imports just fine though. I think there might be a newer version of pyserial that works with both 2.6x and 3.x but I haven't been able to find it, and I am not sure if it is safe to install.

---

### Post by juancarlospaco on 2010-06-26
Try using 2to3 on the .py of serial, 
and put the modified version on the same place as your .py app, name it serial3.py

```

try:
    import serial  # Python2
except ImportError:
    from serial3 import *  # Python3

```

*it works for me once with other lib, i dunno if works for you...*

---

### Post by raf-kig on 2010-06-26
Makes you wonder how all the existing 2.x code will fare after support for it is dropped.

---

### Post by ssam on 2010-06-27
i think all the distros will keep python 2.x around for a long time after they switch to 3.x for the default version.

---

### Post by DanielWaterworth on 2010-06-27
> **ssam said:**
> i think all the distros will keep python 2.x around for a long time after they switch to 3.x for the default version.

yeh, python2 will still be around in 6-8 years.

---

### Post by juancarlospaco on 2010-06-27
**Meerkat +1 will ship Python 3**

---

### Post by Spiritof76 on 2010-06-27
3.12 has been around for mor than a year now.. and available for Ubuntu just as long .. 
There is a new version of pyserial that is supposed to be be compatable with 3.1 but it is in RC2 I tried to download and install it but it failed.   I suppose I will have to wait until it is the repositorys and install pyserial from there.

---

### Post by -grubby on 2010-06-27
Python 3 did away with relative imports without dots:

[quote=Guido]
The only acceptable syntax for relative imports is from .[module] import name. All import forms not starting with . are interpreted as absolute imports. (PEP [noparse]0328[/noparse])
[/quote]

---

### Post by soltanis on 2010-06-27
Working with Python 3 is frustrating because the thing that made Python really good -- the huge amount of libraries and bindings to external APIs -- has to be redone from scratch. Straight 2to3 conversions on those libraries tend not to work as well (I've tried).

I'm sticking to Python 2.6, personally. More support, more libraries, that's where I'm at.

---

### Post by DanielWaterworth on 2010-06-28
Python programmers are stuck in the cruel position of choosing between a nicer language and more libraries. Often large libraries are waiting for smaller dependencies to be ported. I think this is the case with Django where they are waiting for the mysql bindings.

---


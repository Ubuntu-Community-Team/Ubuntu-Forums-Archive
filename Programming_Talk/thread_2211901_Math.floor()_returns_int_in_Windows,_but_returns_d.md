---
title: "Math.floor() returns int in Windows, but returns double in Linux?!"
date: 2014-03-18
forum: Programming Talk
---

### Post by pavelexpertov on 2014-03-18
Hello, I searched the net to find an answer to this tiny annoyance, but unfortunately I did not find one. 
Basically, I was doing some programming in Python 3.3 by writing small algorithms (like zeller one) and I managed to make it work on windows, whereas in Linux, I stumbled upon the problem. Basically I spent 2 hours debugging this thing until I found out that Math.floor() return double value in Linux compared to Windows, where the function returns int!!!! I find it very annoying wasting my time debugging. Anyone who knows about this, please can you explain this to me on why this happens. Thank you.

PS. At least I learned my lesson, should use casting functions next time to make sure the values are right.

---

### Post by ofnuts on 2014-03-18
I wonder what version of Python you are using:
```

>>>python3
Python 3.2.3 (default, Feb 28 2014, 00:21:38) 
[GCC 4.7.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.          
>>> import math
>>> x=math.floor(3.141592654)
>>> print (x)
3
>>> print(type(x))
<class 'int'>

```

Btw, Python v2 (which is still the default Python in Linux) returns a float in math.floor(), so maybe you are not using Python v3 as you think.

PS: Casting is a bad idea, it just hides the problem until it blows  in your face later.

---

### Post by The Cog on 2014-03-18
In python 2.7, math.floor() returns <type 'float'>.

To run python3 in Linux, the command is "python3", not "python". I believe this is part of the python3 specification.

---

### Post by ssam on 2014-03-18
> **The Cog said:**
> In python 2.7, math.floor() returns <type 'float'>.

To run python3 in Linux, the command is "python3", not "python". I believe this is part of the python3 specification.

python was meant to always give python 2.x, and python3 for python 3.x. But some linux distros (arch) though it would be a good idea to make python point to python 3.x. So its safest to use python2 to get python 2.x (although this may not work on some older linux distros).
[http://legacy.python.org/dev/peps/pep-0394/](http://legacy.python.org/dev/peps/pep-0394/)

---

### Post by pavelexpertov on 2014-03-18
Hello, in Linux, I usually type in python3.3, but even if I typed python3, I still get the same new version of python:
```

pavel@pavel-OptiPlex:~$ python3.3
Python 3.3.2+ (default, Feb 28 2014, 00:53:38) 
[GCC 4.8.1] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>

```

Edit: Weird, I used print(type(var)) to find out what type of value I would get, but unfortunately it's int when using Math.floor(). I need to recheck the code I wrote in the first place.

---

### Post by pavelexpertov on 2014-03-18
Update: I checked my code again and now math.floor() produces int value rather than double. Damn it, and I have seen it produce the double value like 2 days ago. It seems like an old good fix of 'rebooting computer' helps. Thanks for posting guys!!!!!!!!!!!!!!!!!!!!!!!!
plus got rid of casting in it since it's not needed.

---

### Post by trent.josephsen on 2014-03-20
> **ssam said:**
> python was meant to always give python 2.x, and python3 for python 3.x. But some linux distros (arch) though it would be a good idea to make python point to python 3.x
The PEP you linked doesn't back up that assertion:
> 
Similarly, the more general python command should be installed whenever any version of Python is installed and should invoke the same version of Python as **either** python2 **or** python3.
**For the time being**, it is recommended that python should refer to python2[...]
[A]ll new code that needs to invoke the Python interpreter **should not specify python, but rather should specify either python2 or python3**
I'm pretty sure there was never any intention to make python refer to python2 forever.

---


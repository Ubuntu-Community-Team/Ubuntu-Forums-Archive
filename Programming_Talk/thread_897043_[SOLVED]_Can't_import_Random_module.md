---
title: "[SOLVED] Can't import Random module"
date: 2008-08-21
forum: Programming Talk
---

### Post by azurepancake on 2008-08-21
Hello all,

Starting last week, I decided I would devote my self to learning some programming. I heard Python was a great language to start with, so I have been trying to learn as much as I can - using [http://en.wikibooks.org/wiki/Non-Progra](http://en.wikibooks.org/wiki/Non-Progra) ... for_Python as my guide.

Today, I have started the section about importing and using modules. Here is a link if your interested, [http://en.wikibooks.org/wiki/Non-Progra](http://en.wikibooks.org/wiki/Non-Progra) ... ng_Modules. I seem to be having trouble loading and working with modules, here is a bit of code at the end of that section, in which I am trying to get working:

```

from random import randint
number = randint(0, 99)
guess = -1
while guess != number: 
    guess = input ("Guess a number: ")
    if guess > number:
        print "Too high"
    elif guess < number:
            print "Too low"
print "Just right"
```

When I attempt to run it, I get the following error: 

```
Original exception was:
Traceback (most recent call last):
  File "high_low.py", line 1, in <module>
    from random import randint
  File "/usr/lib/python2.5/random.py", line 43, in <module>
    from math import log as _log, exp as _exp, pi as _pi, e as _e, ceil as _ceil
ImportError: cannot import name log
```

I attempted to search for this error, using Google - but no luck. Am I making a silly mistake? Perhaps I am missing some kind of important add-on for Python? If anyone can shoot me some advice, I will greatly appreciate it.

Thanks in advance!

---

### Post by WW on 2008-08-21
Interesting.  Do you have a file called "math.py" in the same directory where you are running this program?  If so, change the name of the file.

I can recreate your error like this:
```

$ touch math.py
$ python
Python 2.5.1 (r251:54863, Jul 31 2008, 23:17:43) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from random import randint
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/random.py", line 43, in <module>
    from math import log as _log, exp as _exp, pi as _pi, e as _e, ceil as _ceil
ImportError: cannot import name log
>>> 

```
By saying "touch math.py", I create the file math.py.  The random module tries to import some functions from the math module, but it finds my "math.py" file first, which is the wrong one.

Also check out [this thread](http://ubuntuforums.org/showthread.php?t=896703).  It's like deja vu all over again. :)

---

### Post by Wybiral on 2008-08-21
> **WW said:**
> Interesting.  Do you have a file called "math.py" in the same directory where you are running this program?  If so, change the name of the file.

lol, I've done that exact same thing before (when I have a folder of junk Python files I've been playing with I don't think about their names too much, and sometimes they collide with a standard module).

---

### Post by pmasiar on 2008-08-21
> **Wybiral said:**
> lol, I've done that exact same thing before (when I have a folder of junk Python files I've been playing with I don't think about their names too much, and sometimes they collide with a standard module).

... so it is good practice to name modules in a way it will never clash (myxxx.py), and/or check core library names before naming program.

---

### Post by azurepancake on 2008-08-22
Doh. That worked the magic. Thanks a lot!

That previous thread really is like deja vu. My apologies for a almost identical-double post! Need to work on my forum searching skills.

Thanks again.

---


---
title: "Python + Psyco"
date: 2008-12-28
forum: Programming Talk
---

### Post by pokerbirch on 2008-12-28
I'm fairly new to Python and am experimenting with various speed tests as i have a couple of projects that can be time critical.

I realise that i can write these critical sections in C, but i would like to prove/disprove Python optimization before going down that route.

I'm currently playing with Psyco. I have installed it via Synaptic and it is importing ok, however my function attributes do not match the documentation:

```

if __name__ == '__main__':
    try:
        import psyco
        psyco.full()
    except ImportError:
        pass
--------------------------------------------
Traceback (most recent call last):
  File "psyco.py", line 7, in <module>
    psyco.full()
AttributeError: 'module' object has no attribute 'full'

```

Google isn't helping much....any suggestions?

---

### Post by Greyed on 2008-12-28
```

{grey@morpheus:~} python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49)
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import psyco
>>> psyco.full()
>>> print "foo"
foo

```

Dunno what to tell you.  You're not running 64bit, are you?

---

### Post by pokerbirch on 2008-12-28
```
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import psyco
>>> psyco.full()
>>> print('hmmmmmm....')
hmmmmmm....
>>> 

```

I'm using Editra because it has nice code completion...i guess i've just found a bug??

---

### Post by pokerbirch on 2008-12-28
Derrrrr, i feel such an idiot. Opened the script in Geany and had the same problem when i ran it. It was then that i realised that i'd named my own script 'psyco.py' so it was actually importing itself! I should've realised because Editra was offering me auto-completes that were in my own code!
All i can say is: **[SIZE="4"]D'OH![/SIZE]**

---

### Post by pmasiar on 2008-12-28
> **pokerbirch said:**
> I'm fairly new to Python and am experimenting with various speed tests as i have a couple of projects that can be time critical.

I realise that i can write these critical sections in C, but i would like to prove/disprove Python optimization before going down that route.

Another way is to use Cython for bottleneck part (after you profiled and identified them of course - not guessed). Cython is a subset of (extended) Python which is compiled to C. Wikipedia knows more.

---

### Post by crazyfuturamanoob on 2008-12-29
I had a weird "bug" with importing things.

If I import with "import math" then it may NOT be global or work.
But if I import it like this "import math as math" then it will work.

Dunno why it works but it still works in some cases.

---


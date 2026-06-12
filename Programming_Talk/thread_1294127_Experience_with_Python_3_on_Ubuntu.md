---
title: "Experience with Python 3 on Ubuntu?"
date: 2009-10-17
forum: Programming Talk
---

### Post by A_Fiachra on 2009-10-17
I apologize if this is is a bit off topic here, but what has been your experience using Python 3 while maintaining python 2.x for system utilities?

I would like to start developing in Python 3.1 and porting some apps  from Python 2.x, but I want to avoid land mines with system utilities that are dependent on Python.

TIA

==AF

---

### Post by Can+~ on 2009-10-17
You can run python scripts with

[PHP]python -3 myscript.py[/PHP]

To warn about incompatibilities with python 3.

---

### Post by A_Fiachra on 2009-10-18
> **Can+~ said:**
> You can run python scripts with

[php]python -3 myscript.py[/php]To warn about incompatibilities with python 3.

Thank you.

However running:

```

sudo find /usr/lib -name "*.py" -exec python -3 {} \;

```

tells me there are a LOT of things that would break if I made python 3.1 my default Python.

Makes me think I should just build from source and install in /opt/python3


Thoughts??

==AF

---

### Post by j7%&lt;RmUg on 2009-10-18
If i wanted to port stuff to python 3.1 then thats what i would do, i just ran one of my python programs with the -3 flag(thanks for that) and i found out cpickle is deprecated in 3.0.

---

### Post by casevh on 2009-10-18
It's easy to install alternative versions of Python to a different location and not replace the system version. Short version:

1) Get source and and untar, etc.
2) ./configure --prefix=/usr/local --enable-unicode=ucs4
3) make
4) make altinstall

This will install a new version of Python in /usr/local/bin and leave the name as python3.1. I usually create a symlink so I can just type py31.

casevh

---

### Post by wmcbrine on 2009-10-18
...none of which is necessary. Seriously, it's not an issue. Just install Python 3 from the repos. It will not become the system's default Python. It will not interfere with the system's default Python. Just type "python3" instead of "python" when you want to use it. You can do the same with other versions, too -- I have python2.4, python2.5, python2.6 and python3 all installed simultaneously. 2.6 is the default. None of them interfere with each other.

---


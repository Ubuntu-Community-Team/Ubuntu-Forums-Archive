---
title: "Python: bash-shell-like less functionality in the python shell"
date: 2010-06-25
forum: Programming Talk
---

### Post by narnie on 2010-06-25
Hello,

Is there some type of functional way to read things in the Python shell interpreter similar to less or more in the bash (and other) command line shells?

Example:
```
>>> import subprocess
>>> help(subprocess)
...
[pages of stuff to read]
...

```

I'm hoping so as I hate scrolling and love how less works with simple keystrokes for page-up/page-down/searching etc.

With thanks,
Narnie

---

### Post by Bachstelze on 2010-06-25
Which version of PYthon are you using? That's exactly what it does for me.

---

### Post by wmcbrine on 2010-06-25
> **Bachstelze said:**
> That's exactly what it does for me.+1

In fact, I think it's actually using less. Let's see... yep:

```
31200 pts/0    S+     0:00  |   \_ python
31203 pts/0    S+     0:00  |       \_ sh -c less
31204 pts/0    S+     0:00  |           \_ less
```

---

### Post by narnie on 2010-06-25
> **Bachstelze said:**
> Which version of PYthon are you using? That's exactly what it does for me.

I'm using

> Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2

I see the problem. I tried it in a terminal, and got what you said.

I'm using IDLE and its Python shell (I really like/need code completion, I'm just so used to it in the shell and right my own complete scripts in bash).

I just type help(subp[tab key]) subprocess (just wish it would do it for importing modules) and love it filling out the module for me. Go ahead and say it, I'm lazy. But it also helps with coding errors.

I could always use my fav terminal, but I'm just wondering if there were something for the python shell environment in IDLE. I wonder why they wouldn't implement that in IDLE, too.

Does anyone recommend a good IDE(free as in beer, but preferably FLOSS) for Gnome? I was trying Eric (even though it is KDE) but code completion behaved poorly in Gnome. 

Tried Drpython and it look promising but kept crashing with code completion (plus it oddly didn't use tab for code completion which I would find irritating).

Thanks,
Narnie

---

### Post by narnie on 2010-06-25
> **wmcbrine said:**
> +1

In fact, I think it's actually using less. Let's see... yep:

```
31200 pts/0    S+     0:00  |   \_ python
31203 pts/0    S+     0:00  |       \_ sh -c less
31204 pts/0    S+     0:00  |           \_ less
```

Strange, from the command line, I did "ps uxf|grep -A 10 python" and I don't get the above. I just get

3442  0.1  0.3   5868  3248 pts/0    Ss   21:12   0:00  \_ bash
3505  0.0  0.3   7992  3828 pts/0    S+   21:18   0:00      \_ python

I don't have a sh subprocess and less. How did you get that?

Thanks,
Narnie

---

### Post by wmcbrine on 2010-06-26
Well, I just did "help(subprocess)" in python, and in another shell, "ps fax".

---

### Post by geirha on 2010-06-26
Here's the source of pydoc.py in python 2.6.5 [http://svn.python.org/view/python/tags/r265/Lib/pydoc.py?view=markup](http://svn.python.org/view/python/tags/r265/Lib/pydoc.py?view=markup)

Browse down to the getpager function. That's the code it uses to determine what type of pager to use. Try those expressions until you find which it triggers on.

For me:
```

>>> import sys, os, types
>>> type(sys.stdout) is not types.FileType
False
>>> not sys.stdin.isatty() or not sys.stdout.isatty()
False
>>> os.environ.get('TERM') in ('dumb', 'emacs')
False
>>> sys.platform == 'win32' or sys.platform.startswith('os2')
False
>>> hasattr(os, 'system') and os.system('(less) 2>/dev/null') == 0
True

```
Thus it'll use less.

---

### Post by narnie on 2010-06-26
> **wmcbrine said:**
> Well, I just did "help(subprocess)" in python, and in another shell, "ps fax".

Ah, I figured it out. You did it while you were browsing the help within python.

I misunderstood. I thought what was meant above was that the python shell runs from the beginning with less. What was really meant was that it runs it when needed (as in when doing a help call with long output).

Under those circumstances, I got:

```


$ $ ps uxf
. . .
xxx    3442  0.0  0.2   5868  2832 pts/0    Ss   Jun25   0:00  \_ bash
xxx    6121  0.7  0.4   9260  5052 pts/0    S+   09:02   0:00  |   \_ python
xxx    6124  0.0  0.0   1828   516 pts/0    S+   09:02   0:00  |       \_ sh -c less
xxx    6125  0.0  0.0   3580   928 pts/0    S+   09:02   0:00  |           \_ less
...

```

as well.

Narnie

---

### Post by narnie on 2010-06-26
> **geirha said:**
> Here's the source of pydoc.py in python 2.6.5 [http://svn.python.org/view/python/tags/r265/Lib/pydoc.py?view=markup](http://svn.python.org/view/python/tags/r265/Lib/pydoc.py?view=markup)

Browse down to the getpager function. That's the code it uses to determine what type of pager to use. Try those expressions until you find which it triggers on.

For me:
```

>>> import sys, os, types
>>> type(sys.stdout) is not types.FileType
False
>>> not sys.stdin.isatty() or not sys.stdout.isatty()
False
>>> os.environ.get('TERM') in ('dumb', 'emacs')
False
>>> sys.platform == 'win32' or sys.platform.startswith('os2')
False
>>> hasattr(os, 'system') and os.system('(less) 2>/dev/null') == 0
True

```
Thus it'll use less.

I am a Linux user, so the last one was for me.
From IDLE's python shell, I did:

```
>>> pager

Traceback (most recent call last):
  File "<pyshell#126>", line 1, in <module>
    pager
NameError: name 'pager' is not defined
>>> pager = lambda text: pipepager(text, 'less')
>>> help(subprocess)
```

But sadly, no pager. Perhaps there is no way to make IDLE do this. Oh well. If there is no other solution, I guess I'll use the shell for browsing code since it works there.

Wonder why Idle, which is made by the python project themselves if I remember right, would not give it a pager function.

Narnie

PS,
Just tried "pager" from a python prompt in the terminal window running python and the pager variable is not set there either. Strange.

---


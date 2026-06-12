---
title: "Python newbie, help needed"
date: 2011-05-01
forum: Programming Talk
---

### Post by hyperAura on 2011-05-01
Hi guys, 

I decided to start programming in Python as I have a project in my mind and I think that Python is the right language for it.

For programming I personally use IDE's, so I installed IDLE 3 for Python.

My problem is that when I run in IDLE the following command

```
>>>print "hello world"
```I get syntax error, whereas if I run the same command in a terminal window, it runs ok..

Does anyone know what the problem might be?? Or maybe a better editor if it exists?

Thanks

---

### Post by dv3500ea on 2011-05-01
In python 3 you need to have brackets around what you are printing because print is now a function.

Use:

```
print("hello world")
```

instead.

---

### Post by hyperAura on 2011-05-01
ok now I am trying to use the sys.exit() function..

On top of my code I did:

import sys

...
Code
sys.exit()
...

The program exits but I also get the following message which I don't know if it is the normal behavior:


> Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    parseAddress("://")
  File "/home/hyperaura/Python/webparse.py", line 7, in parseAddress
    sys.exit()
SystemExit


The text is in red color so I guess that I might not be using the exit function properly..
Also the sys.exit() is not highlighted whereas all the other functions are written in purple..

thanks

---

### Post by hakermania on 2011-05-01
I know almost nothing about python, but maybe ou should provide an exit status/number?
like
sys.exit(0)

---

### Post by hyperAura on 2011-05-01
hey, I have tried your suggestion but the output remains the same..

---

### Post by cgroza on 2011-05-01
> **hyperAura said:**
> hey, I have tried your suggestion but the output remains the same..
Open a terminal, start python3, and try the function call. If it is okay, it is an IDLE thing.

---

### Post by simeon87 on 2011-05-01
You are using sys.exit correctly: [http://docs.python.org/library/sys.html#sys.exit](http://docs.python.org/library/sys.html#sys.exit) However, sys.exit doesn't exit the system but it just raises a SystemExit exception (as you've seen). Normally, this can exit the system but it may be that IDLE shows the exception instead. This is also in the docs:

> Since exit() ultimately “only” raises an exception, it will only exit the process when called from the main thread, and the exception is not intercepted.

It's likely that execution is handed over to IDLE when you raise SystemExit.

---

### Post by cgroza on 2011-05-01
> **simeon87 said:**
> You are using sys.exit correctly: [http://docs.python.org/library/sys.html#sys.exit](http://docs.python.org/library/sys.html#sys.exit) However, sys.exit doesn't exit the system but it just raises a SystemExit exception (as you've seen). Normally, this can exit the system but it may be that IDLE shows the exception instead. This is also in the docs:



It's likely that execution is handed over to IDLE when you raise SystemExit.
So this code will stop application exit?

```


import sys

try:
     sys.exit(0)
except SystemExit:
     #do something else?



```

---

### Post by hyperAura on 2011-05-01
hey cgroza I am guessing that the interrupt is not written like this but instead it is going to be an interrupt from a peripheral such as the keyboard or a mouse click..

I believe that the code you posted will just exit, without performing what is after the sys.exit() line..

---

### Post by nvteighen on 2011-05-02
sys.exit means 'interrupt the thread regardless of what stack frame we are'. In a single-threaded program, that will interrupt the whole program. And it takes an integer as argument so you can return a value to whatever called the thread or program.

Different thing is how it is implemented in Python (an exception). You shouldn't care about that: you'll get a SystemExit only when you've directed so (via sys.exit or by manually raising SystemExit), so a priori it makes little sense to catch it.

---

### Post by hyperAura on 2011-05-05
hey thanks a lot.. I was just worried with the traceback which appears in red color, whether my code was correct

---

### Post by andrewgail on 2011-05-06
Yes, Python is great programming language for any type project. Python encourages program reusability by implementing modules and packages. A big set of modules has already been developed and is provided as The Standard Python Library, which is allotment of the Python distribution.

---


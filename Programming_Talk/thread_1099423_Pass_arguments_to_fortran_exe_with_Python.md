---
title: "Pass arguments to fortran exe with Python"
date: 2009-03-18
forum: Programming Talk
---

### Post by sambarluc on 2009-03-18
Hi everybody,
this is a very newbie question, I guess. I do not have experience with scripting languages, but I am trying to learn Python, and use lots of fortran code in my work. So, let's say that I am not used to high level programming. What I expect Python to do, is something like: run a fortran code, give it the parameters it needs, process the output from fortran with another script and then cat a series of files together.
I guess this is not a very exotic task, but I can't find a tutorial or something like that focusing on this kind of things.
I am getting a bit lost in the documentation, I fear...
Thanks!

AC

---

### Post by ghostdog74 on 2009-03-18
to call external programs, use the subprocess module.

---

### Post by WW on 2009-03-18
Expanding on ghostdog74's suggestion to use the [subprocess](http://docs.python.org/library/subprocess.html) module...

To simply run a command, you can use the call() method:
```

>>> import subprocess
>>> subprocess.call(['ls','-a'])
.  ..  a.txt  stuff.dat
0
>>> 

```
If you want to get the output of the command into Python, use Popen():
```

>>> p = subprocess.Popen(['ls','-a'],stdout=subprocess.PIPE)
>>> result = p.stdout.readlines()
>>> result
['.\n', '..\n', 'a.txt\n', 'stuff.dat\n']
>>> 

```

---

### Post by sambarluc on 2009-03-18
Wow, finally I am getting closer to what I want. Thanks!
But what about the input prompt of fortran? The fortran exe that I call asks for some parameters at the prompt. I have seen some module that emulate typing, but that seems a very complicated solution.
AC

---

### Post by the_unforgiven on 2009-03-18
> **sambarluc said:**
> Wow, finally I am getting closer to what I want. Thanks!
But what about the input prompt of fortran? The fortran exe that I call asks for some parameters at the prompt. I have seen some module that emulate typing, but that seems a very complicated solution.
AC
You can use the Popen.stdin for it.
For example:
```

proc = subprocess.Popen(['passwd'], shell=True, close_fds=True, **stdin=subprocess.PIPE**, stdout=subprocess.PIPE)
print proc.stdout.readlines()
**proc.stdin.write('newpasswd')**
print proc.stdout.readlines()
**proc.stdin.write('newpasswd')**
status = proc.wait()
if status == 0:
    print "Password changed successfully"

```
**BIG FAT WARNING: This should be used carefully; I needed a program that reads input from stdin, so, I chose passwd - which was the first thing that came to my mind.**

For more details, check out the examples given at the end of this page:
[http://docs.python.org/library/subprocess.html](http://docs.python.org/library/subprocess.html)

HTH ;)

---

### Post by sambarluc on 2009-03-18
Thank you very much, I think I have all the pieces of the puzzle, now.
AC

---


---
title: "PyGTK with two windows"
date: 2009-06-15
forum: Programming Talk
---

### Post by master_kernel on 2009-06-15
Right now I'm having trouble: I have a deadline of June 22 to get KernelCheck out, and for the life of me I can't figure out how to get this working. There are two main scripts: main.py and build.py. When the user runs 'gksu kernelcheck' as a normal user, main.py runs but does not open build.py. When the user runs 'gksu kernelcheck' as the root user, main.py runs and DOES open build.py. What I would like to have happen is this:

[LIST]
[*]User runs gksu kernelcheck as a *normal* user
[*]main.py runs
[*]User clicks apply, build.py is called, main.py is hidden/closed
[/LIST]

Here is segment of main.py under consideration:
```
os.system('python ' + KCHECK_SCRIPTS + 'build.py ' + data_temp + ' &')
gtk.main_quit()
```


My guess is that it's the '&' at the end that's giving the trouble. When I remove it, KernelCheck runs fine, besides the fact that the previous window (main.py) is still open. This works fine under Ubuntu, but it doesn't on either MEPIS or Debian. Does anyone know of an alternative way to write this?

**EDIT:** I ended up solving this by putting the conflicting lines into the kernelcheck script (/usr/bin/kernelcheck) instead of main.py.
Thanks,
MK

---

### Post by unutbu on 2009-06-15
According to [http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess),
users are encouraged to use the subprocess module instead of os.system. Perhaps it will allow you to avoid the problem?

Since I don't have a MEPIS or Debian installation, I can't check how this works on those platforms, but this works in Ubuntu:

[PHP]#!/usr/bin/env python
from subprocess import Popen
proc=Popen('sleep 100 &', shell=True, )
proc.communicate()

for x in range(10):
    print(x)[/PHP]

You will see the numbers 1..10 printed, as ps shows sleep 100 running in the background.
So maybe try changing 

[PHP]os.system('python ' + KCHECK_SCRIPTS + 'build.py ' + data_temp + ' &')[/PHP]

to

[PHP]from subprocess import Popen
proc=Popen('python ' + KCHECK_SCRIPTS + 'build.py ' + data_temp + ' &', shell=True, )
proc.communicate()[/PHP]

---

### Post by master_kernel on 2009-06-15
> **unutbu said:**
> According to [http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess),
users are encouraged to use the subprocess module instead of os.system. Perhaps it will allow you to avoid the problem?

Since I don't have a MEPIS or Debian installation, I can't check how this works on those platforms, but this works in Ubuntu:

[PHP]#!/usr/bin/env python
from subprocess import Popen
proc=Popen('sleep 100 &', shell=True, )
proc.communicate()

for x in range(10):
    print(x)[/PHP]

You will see the numbers 1..10 printed, as ps shows sleep 100 running in the background.
So maybe try changing 

[PHP]os.system('python ' + KCHECK_SCRIPTS + 'build.py ' + data_temp + ' &')[/PHP]

to

[PHP]from subprocess import Popen
proc=Popen('python ' + KCHECK_SCRIPTS + 'build.py ' + data_temp + ' &', shell=True, )
proc.communicate()[/PHP]
This still sufferred from the same bug. I'm starting to think this is a bug in gksu rather than KernelCheck...

When I run KernelCheck with 'su -c kernelcheck' it runs fine.

---

### Post by unutbu on 2009-06-15
Just for laughs, what happens if you change the command to 

[PHP]os.system('gksu python ' + KCHECK_SCRIPTS + 'build.py ' + data_temp + ' &')  [/PHP]

---

### Post by master_kernel on 2009-06-15
> **unutbu said:**
> Just for laughs, what happens if you change the command to 

[PHP]os.system('gksu python ' + KCHECK_SCRIPTS + 'build.py ' + data_temp + ' &')  [/PHP]
Same thing. gksu sees the program end, but doesn't see that it started a program in the background, and ends up closing the whole thing.

**EDIT:** I ended up solving this by putting the conflicting lines into the kernelcheck script (/usr/bin/kernelcheck) instead of main.py. However, I don't want to mark this as solved until I'm sure that popen.communicate() implies popen.wait().

---


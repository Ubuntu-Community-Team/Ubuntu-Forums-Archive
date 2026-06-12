---
title: "python: get pid of process"
date: 2007-06-04
forum: Programming Talk
---

### Post by htor on 2007-06-04
Are there "python ways" (without use pidof/ps) to get the pid of some process?

---

### Post by ghostdog74 on 2007-06-04
the mostly used method is to parse ps,pidof,or even /proc/<pid> , at least AFAIK for other processes not started by your script. If you want to find the pid of a process started by your script, you can use os.getpid(), os.getppid() etc..check the os module docs.

---

### Post by htor on 2007-06-04
> **ghostdog74 said:**
> the mostly used method is to parse ps,pidof,or even /proc/<pid> , at least AFAIK for other processes not started by your script. If you want to find the pid of a process started by your script, you can use os.getpid(), os.getppid() etc..check the os module docs.

Thanks, I have an other question. 
if I use such function:
```
def process_num(process):
	return os.system('pidof %s |wc -w' % process)
```

it returns the output (that I need) and then it returns the exit status of the process. How can I make pyhton to omit the exit status of the process?

---

### Post by bashologist on 2007-06-04
> **htor said:**
> Thanks, I have an other question. 
if I use such function:
```
def process_num(process):
	return os.system('pidof %s |wc -w' % process)
```

it returns the output (that I need) and then it returns the exit status of the process. How can I make pyhton to omit the exit status of the process?

You would have to use os.popen afaik "var = os.popen("echo blah").read()". And why wc -w? Maybe there's a python way? You could count the words with "len(string.split())"?

---

### Post by cwaldbieser on 2007-06-04
> **bashologist said:**
> You would have to use os.popen afaik "var = os.popen("echo blah").read()". And why wc -w? Maybe there's a python way? You could count the words with "len(string.split())"?

The subprocess module is meant to replace os.popen:

```

pipe = Popen(cmd, shell=True, stdout=PIPE).stdout
output = pipe.read()

```

---

### Post by bashologist on 2007-06-04
> **cwaldbieser said:**
> The subprocess module is meant to replace os.popen:

```

pipe = Popen(cmd, shell=True, stdout=PIPE).stdout
output = pipe.read()

```

Alright. To get these names you would have to import subprocess like this:
```
from subprocess import *
pipe = Popen("echo blah", shell=True, stdout=PIPE).stdout
output = pipe.read()
```

---

### Post by libertyaikido on 2007-10-24
You could also use the commands module

```

import commands

def process_num(process):
    return commands.getoutput('pidof %s |wc -w' % process)

```

That will give you the output of the command without the exit status.

I'm sure you've long solved the problem, but I thought I'd present another method to throw in your bag of tricks.

---

### Post by mythsmith on 2010-07-23
import os
print os.getpid()

[http://docs.python.org/library/os.html#os.getpid](http://docs.python.org/library/os.html#os.getpid)

---

### Post by dosht on 2012-09-06
```
import psutil
[p.pid for p in psutil.process_iter() if "xyz" in str(p.name)]

```
this is similar to ps aux |grep xyz without calling a subprocess

---

### Post by sandyd on 2012-09-06
**Necromancy - thread closed.**

As part of the Ubuntu Forums code of conduct, do not post in threads more than one year old.

---


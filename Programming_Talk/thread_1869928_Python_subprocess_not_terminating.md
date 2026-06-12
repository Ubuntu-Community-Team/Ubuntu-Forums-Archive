---
title: "Python: subprocess not terminating"
date: 2011-10-26
forum: Programming Talk
---

### Post by Nico-dk on 2011-10-26
Several questions here for anyone willing to help out.

**1) Subprocess not terminated**
When i run the below code, Epiphany starts as expected but is never terminated.
The terminate command seems to be ignored, since Done is printed to the terminal.

```
#!/usr/bin/env python

import subprocess
from time import sleep

def call_epi(weburl, time_span):
    epi = subprocess.Popen("epiphany %s" % weburl, shell=True)
    sleep(time_span)

    epi.terminate()

call_epi("http://google.com", 10)

print "done?"
```

Can anyone tell me why epiphany isn't closed down?
What am I missing here?


**2) isn't shell optional?**
If I set shell=False I get the following error

```
Traceback (most recent call last):
  File "browser_loop.py", line 41, in <module>
    browse(weburl, 5)
  File "browser_loop.py", line 37, in browse
    child = subprocess.Popen('epiphany %s' % url, shell=False)
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```

Again, I'm sure it's me being a bit thick, so any help would be appreciated.


*edit*
Forgot to mention that this is in Ubuntu using Python 2.7.0+ (r27:82500, Sep 15 2010, 18:04:55)


Thanks for your time :)

---

### Post by Nico-dk on 2011-10-26
Hmm ... It seems it seems subprocess.Popen starts more than 1 process.

To see the number of processes the script started, I added the following to the call_epi function ... 

```
command = "ps -ef"
print subprocess.call(command.split())
```

Which returned:
0
5614
1

Termintae still doesn't kill anything it seems, since Done is still returned at the end of the script. But killing 5614 from the terminal closes Python (IDLE to be exact) but leaves Epiphany running.

The question now, is how do I kill only the epiphany subprocess and not the python script itself?

---

### Post by Nico-dk on 2011-10-26
This fixed both issues for me ... Not sure why though, so if anyone could elaborate, feel free to do so

```
shell_command = "epiphany " + weburl

def call_epi(weburl, time_span):
    epi = subprocess.Popen(shell_command.split())
```

---

### Post by cgroza on 2011-10-26
That because popen takes a list with the executable name as the first element.
In the first example, you provide the executable name plus the arguments in the same string.
Maybe this confused it about the name of the process and the rest may be implementation defined.

---

### Post by MadCow108 on 2011-10-26
> **Nico-dk said:**
> This fixed both issues for me ... Not sure why though, so if anyone could elaborate, feel free to do so

```
shell_command = "epiphany " + weburl

def call_epi(weburl, time_span):
    epi = subprocess.Popen(shell_command.split())
```

(As I don't know epiphany I'm guessing)
if executed with shell=True, it runs it in a shell.
That means you fork a shell, and that shell then again forks epiphany.
Probably epiphany detaches itself from the shell, so when you kill the shell epiphany does not die with it.

with shell=True epiphany is a direct child of the python process and directly receives the terminate signal and dies.

btw don't use shell=True its horribly insecure.

---

### Post by Nico-dk on 2011-10-26
Aah, makes sense.

So ...

```
epi = subprocess.Popen("epiphany", weburl)
```

... would likely work just as well.

Thanks :)


*edit*
Thanks MadCow108 :)

That's the conclusion I came to too, only for some reason i couldn't start epiphany w/o shell=true (it should be False by default according to the documentation).

It seems it all boils down to me not providing a list for popen.

---

### Post by MadCow108 on 2011-10-26
no this will:
```
epi = subprocess.Popen(["epiphany", weburl])
```

Popen takes a list of strings when called regulary (just like the underlying execve functions).

It may seem akward but it saves you the trouble of sanatizing and quoting your arguments correctly.

---

### Post by Nico-dk on 2011-10-26
Of course, another newbie mistake, forgot the brackets on the list

---


---
title: "Run BASH built-in commands in Python"
date: 2011-03-28
forum: Programming Talk
---

### Post by duanedesign on 2011-03-28
is their a way to run the built-in BASH commands in python? I have tried everything I can think of. I want to run 'history' or 'fc -ln'

just a couple of the things i have tried:

```
subprocess.Popen(['bash','history'],shell=True, stdout=subprocess.PIPE)
```

```
os.system('history')
```

---

### Post by steven1664 on 2011-03-28
duanedesign,

This is from me, I dont profess to be a python genius, but I am ok.  The easiest way I have found to run BASH commands in python is the following:

import os

bashcmd=os.popen("whoami")
print bashcmd.read()

There ya go that is all there is to it.  If you have any other questions for me I would be glad to help.

---

### Post by MadCow108 on 2011-03-28
> **steven1664 said:**
> duanedesign,

This is from me, I dont profess to be a python genius, but I am ok.  The easiest way I have found to run BASH commands in python is the following:

import os

bashcmd=os.popen("whoami")
print bashcmd.read()

There ya go that is all there is to it.  If you have any other questions for me I would be glad to help.
1. whoami is no bash builtin
2. os.popen is deprecated use subprocess

@op:
you could read the .bash_history file ($HISTFILE)

---

### Post by Cheesehead on 2011-03-28
subprocess works. It just requires the whole structure. First you **define** the event, then in another line you **do** the event to create output.
```

from subprocess import Popen, PIPE, STDOUT
shell_command = 'date'
event = Popen(shell_command, shell=True, stdin=PIPE, stdout=PIPE, 
    stderr=STDOUT, close_fds=True)
output = event.stdout.read()
print(output)

```
There are lots of variations. This particular one works in Py2 and Py3.

history is not a bash builtin, and won't be found. Try 'which history' and you will see that it fails.

---

### Post by v8YKxgHe on 2011-03-28
> **Cheesehead said:**
> history is not a bash builtin, and won't be found. Try 'which history' and you will see that it fails.

That's why you shouldn't use "which". Always use "type":

```
$ type history
history is a shell builtin
```

---

### Post by MadCow108 on 2011-03-28
> **Cheesehead said:**
> subprocess works. It just requires the whole structure. First you **define** the event, then in another line you **do** the event to create output.
```

from subprocess import Popen, PIPE, STDOUT
shell_command = 'date'
event = Popen(shell_command, shell=True, stdin=PIPE, stdout=PIPE, 
    stderr=STDOUT, close_fds=True)
output = event.stdout.read()
print(output)

```
There are lots of variations. This particular one works in Py2 and Py3.

history is not a bash builtin, and won't be found. Try 'which history' and you will see that it fails.

have you even tried?
this does not work for history, or else op would probably have not opened this thread..

I do not know why history does not work, alias which is also a builtin works when you use bash -c
strange

---

### Post by duanedesign on 2011-03-29
> @op:
you could read the .bash_history file ($HISTFILE)

Yeah I might just have to.

**EDIT:** I finally found a solution.

```
        from subprocess import Popen, PIPE, STDOUT
        shell_command = 'bash -i -c "history -r; history"'
        event = Popen(shell_command, shell=True, stdin=PIPE, stdout=PIPE, 
            stderr=STDOUT)
            
        output = event.communicate()
```

---


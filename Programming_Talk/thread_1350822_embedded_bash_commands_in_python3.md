---
title: "embedded bash commands in python3?"
date: 2009-12-09
forum: Programming Talk
---

### Post by earthpigg on 2009-12-09
im a supernoob @ python and programming in general, so i dont know the right terms to use when google searching.

my bash-fu is decent, however, so it would behoove me to mix and match the two until my python-fu is up to speed.

lets take an imaginary python script...

```
python3 code
more code

[COLOR="Red"]run /path/to/bashscript.sh or (this) set of bash commands[/COLOR]

back to python code
more code
```

is there a simple way to do this?

---

### Post by geirha on 2009-12-10
```

>>> from subprocess import Popen, PIPE
>>> p = Popen("bash", stdout=PIPE, stdin=PIPE)
>>> p.stdin.write("echo 'hello'\n")
>>> p.stdin.close()
>>> p.stdout.read()
'hello\n'
>>> help("subprocess")

```

Though you are probably much better off doing everything in python.

---

### Post by falconindy on 2009-12-10
Rather than starting a whole new shell, you can execute a single command:
```
p = Popen(['ls', '-l'], stdout=PIPE).communicate()[0]
```
p now contains the results of 'ls -l'. You can pipe it to another command as well:
```
p1 = Popen(['ls', '-l'], stdout=PIPE)
p2 = Popen(['grep', '^d'], stdin=p1.stdout, stdout=PIPE).communicate()[0]
```
p2 now contains the output of 'ls -l | grep ^d'. Notice that you're executing on the second command, not the first.

I wrote a bunch of scripts this way when I was first learning Python. I found it was good practice to go back and remove the multiple Popen executions by replacing them with native Python.

---

### Post by earthpigg on 2009-12-10
great, thanks :D

---


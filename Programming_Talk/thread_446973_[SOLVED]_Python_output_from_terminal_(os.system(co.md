---
title: "[SOLVED] Python output from terminal (os.system(command))"
date: 2007-05-17
forum: Programming Talk
---

### Post by holihue on 2007-05-17
How can I get the output that prints in the treminal?

An Example:

Terminal:

$glxinfo | grep direct
direct rendering: Yes


Python:

>>>import os
>>>os.system('glxinfo | grep direct')
0
>>>



Thanks

---

### Post by WW on 2007-05-17
Use **os.popen** (or one of its variants):
```

>>> import os
>>> p = os.popen('glxinfo | grep direct')
>>> s = p.readline()
>>> p.close()
>>> s
'direct rendering: Yes\n'
>>>

```
Read more about it [here]("http://docs.python.org/lib/os-newstreams.html").

---

### Post by holihue on 2007-05-18
Thanks

---

### Post by thenetduck on 2007-12-06
Thanks this helped me

---

### Post by pcit on 2007-12-19
This help me, too! Thanks!

---

### Post by Majorix on 2007-12-19
Odd thing, doing directly a
[PHP]os.system("glxinfo | grep rendering")[/PHP]
outputs
```
direct rendering: Yes
0
```
by me. I don't know why it outputs a 0, but the info we look for is in the output too.

Maybe you guys have to update your Python interpreter?

---

### Post by engla on 2007-12-19
> **Majorix said:**
> Odd thing, doing directly a
[PHP]os.system("glxinfo | grep rendering")[/PHP]
outputs
```
direct rendering: Yes
0
```
by me. I don't know why it outputs a 0, but the info we look for is in the output too.

Maybe you guys have to update your Python interpreter?
There are three processes running, 1 is python and the other two are in this command 'glxinfo | grep rendering'; you see the combined output, python doesn't read the output from the glxinfo | grep command so it is printed to stdout too. This means the output is not available to python.

---


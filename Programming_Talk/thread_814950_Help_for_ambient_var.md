---
title: "Help for ambient var"
date: 2008-06-01
forum: Programming Talk
---

### Post by furious105 on 2008-06-01
Hi
I need to know if exist a python's function that find the value of $PATH var
and, how can i to assign a new value at $PATH from terminal?

thanks
bye :) :guitar:

---

### Post by pdwerryhouse on 2008-06-01
You can access environment variables in Python with os.environ:

import os

print os.environ['PATH']


To change the PATH variable from the bash shell, use something like:

export PATH=/usr/bin:/bin

to append to it, use:

export PATH=${PATH}:/usr/local/bin

---

### Post by furious105 on 2008-06-01
> **pdwerryhouse said:**
> You can access environment variables in Python with os.environ:

import os

print os.environ['PATH']


To change the PATH variable from the bash shell, use something like:

export PATH=/usr/bin:/bin

to append to it, use:

export PATH=${PATH}:/usr/local/bin


Thank you very much!!!
But I've wrong to write the var name XD
I thought $PWD and wrote $PATH XD
And another bit thing, can i change the value of $PWD from python?
thanks :)

---

### Post by geirha on 2008-06-01
```
os.environ['PWD']= '/new/path/'
```
But that will generally have no effect. Are you sure you don't want to do
```
os.chdir('/new/path/')
os.getcwd()
``` instead?

---

### Post by furious105 on 2008-06-01
> **geirha said:**
> ```
os.environ['PWD']= '/new/path/'
```
But that will generally have no effect. Are you sure you don't want to do
```
os.chdir('/new/path/')
os.getcwd()
``` instead?

Yes...thank you so much :D

---


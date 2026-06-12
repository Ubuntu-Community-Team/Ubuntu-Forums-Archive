---
title: "[python] find all functions in classes"
date: 2008-06-26
forum: Programming Talk
---

### Post by -grubby on 2008-06-26
I've been trying to make something that finds all the functions in a class. I tried a for statement :
```

for function is class :
    print function

```

It didn't work. Any idea how I might actually do this? I'm doing this for my IRC Bot, again, as a command that lists all the possible commands

---

### Post by erginemr on 2008-06-26
If my memory serves me correctly, it was something like **dir(class_name)**.

---

### Post by -grubby on 2008-06-26
Thanks! That did the trick

---

### Post by -grubby on 2008-06-26
Gah. That returns an ugly list including __init__ and such. I tried to do a text.replace("__init__", ""), then a text.remove("__init__"), but to no avail. I can't seem to remove __init__ and others from the list

---

### Post by erginemr on 2008-06-26
You are welcome! Happy programming. :)

---

### Post by erginemr on 2008-06-26
Hmm, so you are saying among the ones you want (functions), it also includes built-in fuctions such as __init__, __doc__? 

If this is the case and the undesired entries are only in __*__ format, then maybe we can think of a fine sieve to eliminate these entries...

---

### Post by -grubby on 2008-06-26
> **erginemr said:**
> Hmm, so you are saying among the ones you want (functions), it also includes built-in fuctions such as __init__, __doc__? 

If this is the case and the undesired entries are only in __*__ format, then maybe we can think of a fine sieve to eliminate these entries...

yes, that's right.

---

### Post by erginemr on 2008-06-26
Perhaps, one can find a more generic tool to remove those entries with the use of "import re" and the regex keyword "__.*__" Yet, to do it manually:

Under Python command line (or by using IDLE);

the following example command
```
import math
dir (math)
```
gives me a list with:

```
a = ['__doc__', '__name__', 'acos', 'asin', 'atan', 'atan2', 'ceil', 'cos', 'cosh', 'degrees', 'e', 'exp', 'fabs', 'floor', 'fmod', 'frexp', 'hypot', 'ldexp', 'log', 'log10', 'modf', 'pi', 'pow', 'radians', 'sin', 'sinh', 'sqrt', 'tan', 'tanh']
```

Once you get the list; using **a.pop(0)** twice will remove the underscored items (built-in functions) from the list. Then you can refer to the items in the list with:
```
for i in a:
   print i
```

---

### Post by -grubby on 2008-06-26
> **erginemr said:**
> Perhaps, one can find a more generic tool to remove those entries with the use of "import re" and the regex keyword "__.*__" Yet, to do it manually:

Under Python command line (or by using IDLE);

the following example command
```
import math
dir (math)
```
gives me a list with:

```
a = ['__doc__', '__name__', 'acos', 'asin', 'atan', 'atan2', 'ceil', 'cos', 'cosh', 'degrees', 'e', 'exp', 'fabs', 'floor', 'fmod', 'frexp', 'hypot', 'ldexp', 'log', 'log10', 'modf', 'pi', 'pow', 'radians', 'sin', 'sinh', 'sqrt', 'tan', 'tanh']
```

Once you get the list; using **a.pop(0)** twice will remove the underscored items (built-in functions) from the list. Then you can refer to the items in the list with:
```
for i in a:
   print i
```

Didn't seem to work. I'm probably using the code wrong. This is the current code I'm using :

[php]
elif cmd == "list" :
    cmds = dir(comd) + dir(opr) + dir(ownr) 
    cmds.pop(0)
    cmds.pop(1)
   for cmds in cmds :
       send(cmds)

[/php]

---

### Post by erginemr on 2008-06-26
1. What do the following return separately:
```
dir(comd)
dir(opr)
dir(ownr)  
```
and after issuing cmds = dir(comd) + dir(opr) + dir(ownr)
```
dir(cmds)
```

2. Depending on the number and whereabouts of underscored variables, you should use
```
cmds.pop(0)
cmds.pop(0)
```
twice because as soon as you pop the first item, the second item becomes the first.

3. Instead of
```
for cmds in cmds : 
       send(cmds) 
```
you should use
```
for i in cmds : 
       send(i) 
```

5. What is send in send(i)? Is it a user-defined function?

---

### Post by -grubby on 2008-06-26
Well, those respective commands return the annoying "__"*"__" in random places in the middle. 

```

['__doc__', '__init__', '__module__', 'chuck', 'contact', 'fortune', 'ls', 'random', 'stfu', 'time', '__doc__', '__init__', '__module__', 'ban', 'deop', 'devoice', 'kick', 'oper', 'topic', 'unban', 'voice', '__doc__', '__init__', '__module__', 'join', 'nick', 'part', 'quit', 'say']

```

---

### Post by geirha on 2008-06-26
try something like
```

a= <the object>
methods= [x for x in dir(a) if not x.startswith('_')]

```

---

### Post by -grubby on 2008-06-26
Well, I got it to work, but it a slightly inconvienent way, I'll try geirha's way in a minute

[php]
elif cmd == "list" :
    cmds = (dir(comd), dir(opr), dir(ownr)) 
    cmds[0].pop(0);cmds[0].pop(0);cmds[0].pop(0)
    cmds[1].pop(0);cmds[1].pop(0);cmds[1].pop(0) 	   
    cmds[2].pop(0);cmds[2].pop(0);cmds[2].pop(0)
    cmds = cmds[0] + cmds[1] + cmds[2]
    send(cmds)
[/php]

And yes, send is a user defined function

---

### Post by ghostdog74 on 2008-06-26
you can use types
```

>>> import types
>>> def f(): print "test"
...
>>> f()
test
>>> type(f) is types.FunctionType
True
>>> f.__class__ is types.FunctionType
True
>>> f.__class__ is types.DictProxyType
False
>>>        
>>> for k,v in globals().iteritems():
...  if v.__class__ is types.FunctionType: print k,v
...
g <function g at 0xb7bedd14>
f <function f at 0xb7bedcdc>
>>> for r in dir():
...  if type(eval(r)) is types.FunctionType: print r
...
f
g

                            

```

---


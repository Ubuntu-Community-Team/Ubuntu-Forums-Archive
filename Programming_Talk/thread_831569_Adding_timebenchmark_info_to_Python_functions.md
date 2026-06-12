---
title: "Adding time/benchmark info to Python functions"
date: 2008-06-16
forum: Programming Talk
---

### Post by bvmou on 2008-06-16
Anyone know what I would add to a Python function so that it prints the time it took to execute the function?  Something like
```

def listcheck(userinput, a=longlist, ?=?):
    if userinput in a:
        print userinput, ?.WhatModule.WhatFunction

def dictcheck(userinput, b=bigdictionary, ?=?):
    if userinput in b:
        print userinput, ?.WhatModule.WhatFunction
```

---

### Post by bvmou on 2008-06-17
Maybe something like this?:

[PHP]>>> def checktime():
...     a = time.time()
...     time.sleep(2)
...     b = time.time()
...     print 'ok', b-a
...
>>> checktime()
ok 1.99522304535
>>> checktime()
ok 1.99956798553
>>> checktime()
ok 2.0004529953
>>> def timetypes(object):
...     a = time.time()
...     if 'teststring' in object:
...             print 'done'
...     b = time.time()
...     print b-a
...
>>> c = ['hello '*100000][0].split()
>>> counter = 1
>>> d = {}
>>> for item in c:
...     d[item+str(counter)]=''
...     counter += 1
...
>>> c[99000]='teststring'
>>> d['teststring']=''
>>> timetypes(c)
done
0.00699615478516
>>> timetypes(d)
done
2.59876251221e-05
>>> c[9]='teststring'
>>> timetypes(c)
done
2.69412994385e-05
[/PHP]

Is there a better way to do this?

---


---
title: "Missing python time module?"
date: 2008-09-06
forum: Programming Talk
---

### Post by SPW06 on 2008-09-06
I am new to python, and I am trying to write a script to remind me when to take a break :lolflag: 

I am using 
```

import time

n =int(3600)

def done:

   print 'Take a break!'

t=threading.Time(n, done)

```
and not

```
t=threading.Timer(n, done)

```
in order to use 
```

t.start()
t.stop()
```

in order to pause/resume the timer when i need to. But, when I try the script, I get 
> 
AttributeError: 'module' object has no attribute 'Time'

It's if if there is no time module. How can I install it?

Also, is there an easy way to output my 'n' Pack to minutes and seconds?

---

### Post by kjohansen on 2008-09-07
Well I think this code will do what you want.

Note: you need to import the threading package not the time package.

```

import threading
n =int(5)
def done():
   print 'Take a break!'
t=threading.Timer(n,done)
t.start()

```

Then you can call t.cancel() wherever you want.  From my look at the threading package there is no threading.Time just threading.Timer, and you can use start and cancel with the timer.

---

### Post by Joeb454 on 2008-09-07
Moved to Programming Talk

---


---
title: "Python - time.sleep doesn't work"
date: 2009-04-19
forum: Programming Talk
---

### Post by dodle on 2009-04-19
[php]import time

print "Hello..."
time.sleep(4)
print "...World[/php]

The output is:
> AttributeError: 'module' object has no attribute 'sleep'

According to the information that I have found, *time.sleep(seconds)* is the way to cause a delay in a program.  Is something wrong with my Python istallation.

on Ubuntu 8.04

---

### Post by unutbu on 2009-04-19
Perhaps there is a file called "time.py" somewhere in your sys.path other than the standard module.

```
import time 
print time
```
should return```

<module 'time' from '/usr/lib/python2.5/lib-dynload/time.so'>
```

---

### Post by dodle on 2009-04-19
D'Oh!  That was exactly my problem.  I had named my script "time.py". >.<

---


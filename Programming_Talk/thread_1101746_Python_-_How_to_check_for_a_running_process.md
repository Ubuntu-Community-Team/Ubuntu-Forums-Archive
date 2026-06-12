---
title: "Python - How to check for a running process?"
date: 2009-03-20
forum: Programming Talk
---

### Post by dodle on 2009-03-20
I'm trying to figure out how to check and see if a program is already running, to keep from executing the program a second time.  

The program that I am trying to check is x11vnc, which is run from the command line.

---

### Post by days_of_ruin on 2009-03-20
> **dodle said:**
> I'm trying to figure out how to check and see if a program is already running, to keep from executing the program a second time.  

The program that I am trying to check is x11vnc, which is run from the command line.

Maybe there are better ways but this works for me:
```
import commands
output = commands.getoutput('ps -A')
if 'x11vnc' in output:
    print "ITS ALIVE!!!"
```

---

### Post by dodle on 2009-03-20
Thanks, so far that works really well.

---

### Post by ghostdog74 on 2009-03-20
if Python is not a must, just do it from the shell
```

# ps -A | awk '/x1nvc/{print "alive";exit}'
alive


```

---


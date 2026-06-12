---
title: "Writing a bash front end in python"
date: 2007-09-16
forum: Programming Talk
---

### Post by Sayers on 2007-09-16
Hello I want to write a python program to do sensors -f every 3 seconds let's say. How would I write that in python?

---

### Post by peabody on 2007-09-16
```

import os, time

while True:
    print os.popen("sensors -f").read()
    time.sleep(3)

```

---

### Post by Sayers on 2007-09-16
Alright could you explain that code now :) it kinda makes sense with important os but what is popen and such

---

### Post by tvrg on 2007-09-16
popen() will run a command
and popen().read() will run a command and read the output

---

### Post by Sayers on 2007-09-16
Ah, makes sense, now do you reccomend a place to learn pyQT because I can't find anything good.

---


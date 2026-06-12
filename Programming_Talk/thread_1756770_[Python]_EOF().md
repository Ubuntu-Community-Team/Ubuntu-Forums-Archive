---
title: "[Python] EOF()"
date: 2011-05-12
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-12
I need to read a file line by line into a dictionary with a while loop.

```
fob = open("file.txt", "r")
dict = {}
while not EOF(fob):
    a = fob.readline()
    b = fob.readline()
    dict[a] = b
```

This is basically what I want to do, but I can't find an EOF command online for python.

---

### Post by simeon87 on 2011-05-12
You don't need it. You can read a file as follows:

```
for line in fob:
    # do something
```

which will walk over all lines in the file.

---


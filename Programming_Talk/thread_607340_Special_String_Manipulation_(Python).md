---
title: "Special String Manipulation (Python)"
date: 2007-11-08
forum: Programming Talk
---

### Post by 1337455 10534 on 2007-11-08
Python (in my opinion) has some pretty funky string manipulation, and I love it.
However, say:
```

a = raw_input("Xact FilePath: ")
os.system("shred #where 'a' would go# -f -u -v -x -z")

```
How do I get the filepath (the str 'a') to pop up in the os.system call??

---

### Post by CptPicard on 2007-11-08
```

os.system("shred #where '%s' would go# -f -u -v -x -z" % a)

```

For multiple values, it takes tuples after %.

---

### Post by 1337455 10534 on 2007-11-08
but a is just one value...
so:
```

#!/usr/bin/env python
import os, time
print "DETH SHRED"
a = raw_input("Xact FilePath: ")
os.system("sudo shred %s -f -u -v -x -z" % a)
b = input("Verify Deth? (Recursive Destruction of Directories as Well) [1:Y, 2:N]: ")
if b == 1:
       os.system("sudo rm -r -f -d -v %s" % a)
       time.sleep(3)
elif b == 2:
       print "Pwn3d."

```

Excellent.

---

### Post by 1337455 10534 on 2007-11-08
Wow. I put that in, it works brilliantly!
Move on to the GUI!!
Is EasyGUI easy? - {Seems retarded, but, I need to know}

---

### Post by LaRoza on 2007-11-09
Yes, EasyGUI is easy. It is not really a complete GUI toolkit, but it is an easy way to do things with a GUI. You can visit my wiki for links on learning and getting it.

---


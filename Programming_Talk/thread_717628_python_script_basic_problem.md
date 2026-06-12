---
title: "python script basic problem"
date: 2008-03-07
forum: Programming Talk
---

### Post by The Titan on 2008-03-07
im having a problem, i just started learning python last night and i can do simple things in idle, but if i just put the stuff into a .py file and try to execute it it doesn't work... i have it so i can execute the file, example:

script:
```

print "Hello World in Python!"
print "Here are 10 numbers, from 0 to 9"
for i in range(10):
    print i,
print "Finished!" 

```output:
```
titan@dungeon:~/Desktop/python_scripts$ ./hello_world.py
Warning: unknown mime-type for "Hello World in Python!" -- using "application/*"
Error: no such file "Hello World in Python!"
Warning: unknown mime-type for "Here are 10 numbers, from 0 to 9" -- using "application/*"
Error: no such file "Here are 10 numbers, from 0 to 9"
./hello_world.py: line 3: syntax error near unexpected token `('
./hello_world.py: line 3: `for i in range(10):'

```

SOLVED: python hello_world.py  der...

---

### Post by ghostdog74 on 2008-03-07
if you want to use ./script.py, put a shebang in your script's very first line (depending on where you installed python)

```

#!/usr/bin/python 

```
or
```

#!/usr/bin/env python

```

---

### Post by The Titan on 2008-03-07
Thank you, that also worked!  and better!

---


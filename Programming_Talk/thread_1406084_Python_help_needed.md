---
title: "Python help needed"
date: 2010-02-13
forum: Programming Talk
---

### Post by arnab_das on 2010-02-13
Hi! 

am learning to use python.

i am using the default gedit text editor (is that okay?)


```
#!/usr/bin/env python
1 name = input('What is your name?\n')
2 print 'Hi, ' + name + '.'
```

this is the script i typed. i saved it as hello.py
now i typed chmod u+x hello.py
next i  typed ./hello.py

however the output i get is: 

```
 File "./hello.py", line 2
    1 name = input('What is your name?\n')
         ^
SyntaxError: invalid syntax
```

what am i doing wrong? plz help.

---

### Post by Zugzwang on 2010-02-13
Remove the leading "1" from line 2 and "2" from line 3. Line numbers like in Basic are not allowed in Python.

---

### Post by arnab_das on 2010-02-13
that was freakin awesome! thank u.

---


---
title: "python error"
date: 2013-08-14
forum: Programming Talk
---

### Post by wingnut2626 on 2013-08-14
Hi guys I have a directory that has some files in it (duh).  Here are the files in that directory(/sampledirectory):


['copyspecial2.py', 'copyspecial.py', 'zz__something__.jpg', 'xyz__hello__.txt', 'solution']

Here is the code that i am trying (Python 2.7):


```


import os
import re
import os.path

 a = os.listdir('/sampledirectory')
result = []
for item in a:
  match = re.search('__(\w+)__', item)
  if match:
  result.append(os.path.abspath(os.path.join('/sampledirectory', item))

```

Here is the Traceback:

```

Traceback (innermost last):
  File "<stdin>", line 4, in <module>
  File "/usr/lib/python2.7/posixpath.py", line 75, in join
    if b.startswith('/'):
AttributeError: '_sre.SRE_Match' object has no attribute 'startswith'


```


The tutorial I'm working with says this works perfectly fine.  Any insight?

---

### Post by alan9800 on 2013-08-14
it seems to me that you've forgotten one parentheses at the end of last line of your piece of code.
In addition to that, the last line isn't correctly indented.

---

### Post by ian-weisser on 2013-08-14
> **wingnut2626 said:**
> ```

  a = os.listdir('/sampledirectory')

```

Is that really the correct path?

Try print(match.group(0)) to see if the matching object is what you expect.

---

### Post by wingnut2626 on 2013-08-14
No it isnt the real path.  I'm at work right now, when I get home I will try that code and see if it works.

---

### Post by ofnuts on 2013-08-16
Variable "b" seems to be the result of a search() or match()" and therefore is not a string (but a MatchObject). You have to extract the relevant match string using its group() method: [http://docs.python.org/2/library/re.html#match-objects](http://docs.python.org/2/library/re.html#match-objects)

---

### Post by ian-weisser on 2013-08-16
Quite right, of course. Corrected my earlier response. Thanks.

---

### Post by wingnut2626 on 2013-08-18
Oh duh!  Thanks

---


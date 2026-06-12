---
title: "Basic python programming - check if directory is empty"
date: 2008-12-23
forum: Programming Talk
---

### Post by chrismyers on 2008-12-23
I want to check for the presence of files in a directory...

Can anyone tell me what I am doing wrong here?

```
#!/usr/bin/python
import os, time, shutil, sys

work_path = '/home/chris/test/'

if os.listdir(work_path)=="":
    print "yes"
else:
    print "No"
```

---

### Post by snova on 2008-12-23
os.listdir returns a list of files/subdirectories, not a string.

Try:

[PHP]import os
path = '/home/chris/test'
if os.listdir(path) == []:
    print "yes"
else:
    print "no"[/PHP]

There are probably more "pythonic" ways to do the comparison, but it works.

---

### Post by Tony Flury on 2008-12-23
listdir returns a list - not a string - so it will never equal ""

you could use 
```

if os.listdir(work_path) = []:

```
or 
```

if not os.listdir(work_path): 

```
or
```

if len(os.listdir(work_path)) > 0:

```

Take your pick - the middle one is pretty common - since an empty list is always evaluated as False.

---

### Post by snova on 2008-12-23
> **Tony Flury said:**
> ```

if os.listdir(work_path) = []:

```

Tiny bug there. ;)

I prefer the second one. Fewer symbols.

---

### Post by Tony Flury on 2008-12-24
Unless otherwise stated - all code posted by me is untested :-) - I will have to add that to me signature :-)

Ty for pointing it out

---


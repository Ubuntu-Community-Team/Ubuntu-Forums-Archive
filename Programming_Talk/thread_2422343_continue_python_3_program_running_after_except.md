---
title: "continue python 3 program running after except"
date: 2019-07-05
forum: Programming Talk
---

### Post by lance bermudez on 2019-07-05
was told to use pass but the program just ends how do I keep it going?

```

import os
import hashlib
import sys

start_path = '/home/lance' # current user home directory
files_dir = []
for path,dirs,files in os.walk(start_path):
    for filename in files:
        files_dir.append(os.path.join(path,filename))
                
def pwalk():
    try:
        for x in files_dir:
            hasher = hashlib.sha256()
            with open(x, 'rb') as openfile:
                content = openfile.read()
                hasher.update(content)
                with open('data.txt', 'a') as f:
                    print(hasher.hexdigest(), x, sep=",", file=f)
    except PermissionError as permission_error:
        print(permission_error)
        pass
    except FileNotFoundError as filenotfounderror:
        pass
        print(filenotfounderror)
    input('Enter to close...')

pwalk()


```

---

### Post by norobro on 2019-07-05
Try putting your try/except block inside the for loop.```
def pwalk():
    for x in files_dir:
        try:
            ...  
```

---

### Post by kpatz on 2019-07-05
When an exception occurs, execution continues at the except line for the associated exception.  Afterward, it continues at the end of the try block, so in your case it will go directly to the input(...) line.  In your case, pass does nothing.  Pass is a do-nothing instruction that is used for a placeholder where a statement is required but you don't want to execute anything.

To keep your for loop running, put the try/except inside the for loop.  Then if an exception occurs, it will abort the current file and move onto the next.  Like this: (I removed the pass statements since they're unneeded).

```
def pwalk():
    for x in files_dir:
        try:
            hasher = hashlib.sha256()
            with open(x, 'rb') as openfile:
                content = openfile.read()
                hasher.update(content)
                with open('data.txt', 'a') as f:
                    print(hasher.hexdigest(), x, sep=",", file=f)
        except PermissionError as permission_error:
            print(permission_error)
        except FileNotFoundError as filenotfounderror:
            print(filenotfounderror)
    input('Enter to close...')

```

---


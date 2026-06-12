---
title: "print directory the .py file is running from"
date: 2008-09-26
forum: Programming Talk
---

### Post by ratmandall on 2008-09-26
Is there anyway of printing the current directory of the python file that's running?

---

### Post by cmat on 2008-09-26
```
import os

# gets the current working dir
print os.getcwd()
```

---

### Post by ratmandall on 2008-09-26
> **cmat said:**
> ```
import os

# gets the current working dir
print os.getcwd()
```

:)

---

### Post by gfa on 2008-09-27
> **cmat said:**
> ```
import os

# gets the current working dir
print os.getcwd()
```

This will give you the calling dir, but if you are working in /home/user/ and execute the file using: 
/path/to/script/foo.py

, you will get: /home/user, instead of /path/to/script/

If you need the dir where your python is, instead you should use:

```
import sys
print sys.path[0]
```

---


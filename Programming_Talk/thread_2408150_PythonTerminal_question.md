---
title: "Python/Terminal question"
date: 2018-12-14
forum: Programming Talk
---

### Post by chokingjaik on 2018-12-14
Hello everyone and thanks in advance for any assistance provided. I'm attempting to list only usernames in terminal...then use that command in a python application. I've run into an issue, hopefully someone can provide assistance letting me know why it won't work or what I can do to get around it.

Why does this work in terminal:
```
eval getent passwd {$(awk '/^UID_MIN/ {print $2}' /etc/login.defs)..$(awk '/^UID_MAX/ {print $2}' /etc/login.defs)} | cut -d: -f1
```

But this does not work as python?:

```
#!/usr/bin/python3
import sys, os
def lisUser():
print ("This is a current list of users on this system: ")
os.system("eval getent passwd {$(awk '/^UID_MIN/ {print $2}' /etc/login.defs)..$(awk '/^UID_MAX/ {print $2}' /etc/login.defs)} | cut -d: -f1")
lisUser()
```

---

### Post by spjackson on 2018-12-15
Your command works in bash but not in sh. os.system invokes sh. This works:
```

os.system("bash -c \"eval getent passwd {$(awk '/^UID_MIN/ {print $2}' /etc/login.defs)..$(awk '/^UID_MAX/ {print $2}' /etc/login.defs)} | cut -d: -f1\"")

```

---


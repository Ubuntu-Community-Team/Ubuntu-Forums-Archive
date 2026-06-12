---
title: "Wildcard Characters with os.chown in Python"
date: 2009-09-15
forum: Programming Talk
---

### Post by Tipo on 2009-09-15
Hey everyone,

I am writing a script that creates several files and sets the ownership to that of the current directory with os.chown

so I'll run a ```
os.chown(".du", uid, gid)
```

however, the script creates multiple files (.du, .du_foo1, .du_foo2, etc). I want to set the ownership for all of them, but os.chown errors out if you give it a wildcard character (like .du*).

Is there any way to set the ownership of all of these files without creating an individual os.chown line for all of the files?

---

### Post by DaithiF on 2009-09-15
Hi, you could use the glob module, like so:
```
import glob
for file in glob.glob('.du*'):
    os.chown(file, uid, gid)

```

---


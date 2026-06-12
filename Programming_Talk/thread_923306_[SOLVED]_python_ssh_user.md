---
title: "[SOLVED] python ssh user"
date: 2008-09-18
forum: Programming Talk
---

### Post by cdenley on 2008-09-18
Is there a way to tell from a python script if the user running it is doing so from an SSH session, and if so, what their IP address is?

---

### Post by cdenley on 2008-09-18
Nevermind. Easier than I thought.
```

#!/usr/bin/env python
import os
host="127.0.0.1"
f=open("/proc/"+str(os.getpid())+"/environ","r")
data=f.read().split("\0")
for line in data:
    parts=line.split("=",2)
    if len(parts)==2 and parts[0]=="SSH_CLIENT":
        host=parts[1].split(" ")[0]
f.close()
print host

```

---


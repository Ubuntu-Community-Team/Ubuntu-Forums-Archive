---
title: "Instructions not working."
date: 2008-06-19
forum: New to Ubuntu
---

### Post by DrMilo on 2008-06-19
Trying to follow the instructions here:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

When I type: gksu "update manager -d"

I get: sudo: update: command not found

I can't get the message they say I should get from update manager and I have every channel enabled as far as I can tell. 

Suggestions?

---

### Post by sisco311 on 2008-06-19
try:
```
gksu update-manager -d
```
from a terminal.

---

### Post by slibuntu on 2008-06-19
Yeah, looks like a simple typo in that instruction.

---


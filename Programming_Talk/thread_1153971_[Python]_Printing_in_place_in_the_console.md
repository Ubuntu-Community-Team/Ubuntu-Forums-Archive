---
title: "[Python] Printing in place in the console"
date: 2009-05-09
forum: Programming Talk
---

### Post by dodle on 2009-05-09
I read a thread here:
[http://www.python-forum.org/pythonforum/viewtopic.php?f=3&t=12881](http://www.python-forum.org/pythonforum/viewtopic.php?f=3&t=12881)

and it got me curious as to how this is accomplished.  Does anyone over here have an answer for this?  I'll make sure to give you credit over in python-forum.org.

**Edit:** Solutions found.

---

### Post by The Cog on 2009-05-09
```
import time, sys

words = ["One", "Two", "Three", "Four", "Five"]

for w in words:
    sys.stdout.write("\x1b[G\x1b[K" + w)
    sys.stdout.flush()
    time.sleep(1)
sys.stdout.write("\x1b[G\x1b[K")

```
Seems to work for me. That funny sequence means move the cursor to the beginning of the line and clear to the end of the line.

As a thought, that might not work on windows. This one just uses ASCII control sequences, not ANSI escape sequences, which is a little clunkier but should work on non-ANSI terminals.
```
import time, sys

words = ["One", "Two", "Three", "Four", "Five"]

wipelen = 0
for w in words:
    sys.stdout.write("\r" + " " * wipelen + "\r" + w)
    sys.stdout.flush()
    wipelen = len(w)
    time.sleep(1)
sys.stdout.write("\r" + " " * wipelen + "\r")

```

---


---
title: "Python close Terminal window"
date: 2013-09-24
forum: Programming Talk
---

### Post by evamvid on 2013-09-24
Hey Everybody,

I need a way for a CLI python script to be able to close a terminal windows after it finishes. I think the easiest way to do this would be to simulate keypresses and use Control + Shift + Q , but I've already tried two ways of doing this, and neither worked. sys.exit leaves the terminal window open.


Thanks!
Evamvid

---

### Post by r-senior on 2013-09-24
Could you exec the python interpreter so that it replaces the current shell process?

For example:

*test.py*
```
import time
time.sleep(3)
```

```

$ exec python test.py

```

I'd probably be annoyed if I ran a script that closed the terminal window but it depends on the context I guess.

---

### Post by ofnuts on 2013-09-25
Kill your parent process: read /proc/self/status(*), get the PPid value... warning: there are environments with terminals in tabs (Konsole in KDE) and you could be killing other sessions...).

(*) "self" is the process that opens the file,  so you cannot use a subprocess to read, otherwise PPid will be your own. But if you know your own PID, you can read  /proc/$pid/status instead form any process.

---


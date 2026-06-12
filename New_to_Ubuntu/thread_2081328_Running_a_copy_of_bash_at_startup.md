---
title: "Running a copy of bash at startup"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by Raphicerus on 2012-11-06
Since I always end up running a command-line Terminal before long, I thought I would add one to the start-up programs. I added an entry called Terminal with the command being /bin/bash - this is in the "Startup applications" menu in 12.04.

This doesn't seem to do anything, though. Am I missing something obvious here?
Google isn't helping this time.

---

### Post by papibe on 2012-11-06
Hi Raphicerus.

What you want is to start a 'gnome-terminal'.

Let us know how it goes.
Regards.

---

### Post by sisco311 on 2012-11-06
EDIT: D'oh! papibe beat me to it. :)


Bash is a shell, a command interpreter.  You need a terminal emulator to run it interactively. The default one in Ubuntu is:
```
gnome-terminal
```

---

### Post by Raphicerus on 2012-11-06
Thanks, papibe and sisco311, for the instant replies.
That worked perfectly!

---


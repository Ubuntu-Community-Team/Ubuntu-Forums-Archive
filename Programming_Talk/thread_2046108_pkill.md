---
title: "pkill"
date: 2012-08-22
forum: Programming Talk
---

### Post by conradin on 2012-08-22
What does pkill do if it cannot kill a process? Does it send any terminal output? Can it?
I tried pkill -v bootpd (thinking -v would be verbose)(lol) and it basically closed everything I was running.

---

### Post by Lars Noodén on 2012-08-22
-v ... LOL

pkill will come back with an error message to stderr if it cannot kill a process.  

Another gotcha to be aware of is that pkill by itself matches a pattern.  If you want to match a process name and only the name, then you need the -x option.

---

### Post by trent.josephsen on 2012-08-22
Notice that pkill can only tell you whether it succeeded in sending a signal to the process; it won't tell you whether the process heeded the signal or not. Use SIGKILL (pkill -9) to send a signal that can't be ignored (pkill uses SIGTERM by default, which processes are free to disregard).

---

### Post by conradin on 2012-08-22
Thanks Guys! That was helpful!

---


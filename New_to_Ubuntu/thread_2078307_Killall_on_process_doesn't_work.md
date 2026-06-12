---
title: "Killall on process doesn't work"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2012-10-30
I installed Jupiter for some laptop battery life management, but I can't use killall to stop it.

typing "jupiter" starts it, but "killall jupiter" says "jupiter: no process found."

How can I kill it without looking up the process ID every time?

---

### Post by iponeverything on 2012-10-30
killall <name> has to match the name in the process table.


it should be column 11 the ouput from "ps auxwww"

---

### Post by kanikilu on 2012-10-30
I have never used jupiter, but I know sometime things can get a little tricky when dealing with things like scripts run through an interpreter (e.g. bash, python, etc.).

Don't know if that applies here, but...

I'd probably try pkill instead of killall, it has an option (-f) to match the full commandline instead of only the process name:

```
pkill -f jupiter
```

---

### Post by localhost8080 on 2012-10-30
failing the two above replies which will both work, you could try running 'top'

top will give you a list of all the running processes
[press ? to get help inside top]
[press k then enter the pid of the task to kill it]

hope that helps / is useful to others

---

### Post by monkeybrain2012 on 2012-10-30
How about "killall jupiter-applet"? You may need sudo too because I believe it belongs to root.

---

### Post by Thrashrokz33 on 2012-10-30
Nice, "pkill -f jupiter" did exactly what I needed. Thanks guys, excellent response time too.

---


---
title: "Bash While Output of a Command"
date: 2012-06-12
forum: Programming Talk
---

### Post by Kodeine on 2012-06-12
Saluton!

So I'm trying to check if a process is running and while it is keep doing something. I'm trying to use the 'pidof' command which returns the PID of a given process name. If there is no process of the name given then it returns nothing. Here's what I've got so far.

```
while [[ $(pidof rhythmbox) != false ]]; do echo foorbar; sleep 3; done
```

However it doesn't work. Anyone know why?

---

### Post by Vaphell on 2012-06-12
drop != false
[ $(pidof ...) ] should be enough

---

### Post by hakermania on 2012-06-12
> **Vaphell said:**
> drop != false
[ $(pidof ...) ] should be enough
Isn't
```

while pidof X > /dev/null 2>&1; do ...

```
correct?

---

### Post by Kodeine on 2012-06-12
> **Vaphell said:**
> drop != false
[ $(pidof ...) ] should be enough

Ah yes that works.

---


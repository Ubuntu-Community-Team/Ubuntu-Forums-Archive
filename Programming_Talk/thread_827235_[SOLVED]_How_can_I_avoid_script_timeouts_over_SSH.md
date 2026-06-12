---
title: "[SOLVED] How can I avoid script timeouts over SSH?"
date: 2008-06-12
forum: Programming Talk
---

### Post by altonbr on 2008-06-12
I'm trying to run a script like this:
```
time ./script.sh /public/ /archives/
```
but my SSH connection keeps timing out after ~53 minutes (~3200 seconds).

How can I run the shell script in the background so that if my connection gets dropped, it keeps running?

---

### Post by CptPicard on 2008-06-12
```

man screen

```

---

### Post by dtmilano on 2008-06-12
or simply
> nohup command &

---

### Post by CptPicard on 2008-06-12
But with nohup you'll have to remember to redirect output to file or you'll lose it... right?

---

### Post by dtmilano on 2008-06-12
Not really, nohup automatically appends output to nohup.out ot $HOME/nohup.out if stdout is a terminal.

---

### Post by altonbr on 2008-06-12
What about appending the script with '&'? Does that give it a pid?

---

### Post by dtmilano on 2008-06-12
Strictly, appending nohup command with '&', runs it in the background and returns the prompt.

> $ nohup sleep 3600 &
nohup: ignoring input and appending output to `nohup.out'
[1] 9870
$ ps
  PID TTY          TIME CMD
 7978 pts/0    00:00:00 bash
 9870 pts/0    00:00:00 sleep
 9880 pts/0    00:00:00 ps
$ jobs
[1]+  Running                 nohup sleep 3600 &


---

### Post by altonbr on 2008-06-12
EDIT: nevermind, the prompt just wasn't showing up until I hit enter a couple of times.

So yeah, that's great! Looks like its doing its thing!

---


---
title: "[SOLVED] How to check if a machine is idle?"
date: 2008-08-28
forum: Programming Talk
---

### Post by cbdonohue on 2008-08-28
How would you check if a Ubuntu machine is currently idle?  If possible I don't want to have to capture input with listeners to see if it is idle...I want the OS to tell me it is idle.

---

### Post by Zugzwang on 2008-08-28
You could read from the virtual file "/proc/loadavg" and parse its data.

---

### Post by cbdonohue on 2008-08-28
Now that file measures the CPU load...but wouldn't there be some CPU load for things like screen savers or other applications running while the machine is idle.  How would you determine it is idle using that file?

I imagine some flag that states the machine is idle...but I can't find anything like that

---

### Post by Reiger on 2008-08-28
You can do:
```

@:/proc$ cat stat | grep 'procs_running'

```

(Note it does start up at least 2 processes!)

That just outputs it, in reality your app would read & parse the file (stat) itself.

---

### Post by cbdonohue on 2008-08-28
So if this prints >2 ... the machine is not idle?

Anyone know if this is how the screen saver checks for idle?

---

### Post by cbdonohue on 2008-08-28
Using the 'w' command may be a solution.

```

$ w
 19:23:44 up 2 days,  6:45,  2 users,  load average: 0.36, 0.43, 0.27
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
chris    tty7     :0               Tue12    0.00s 47:42m  0.18s x-session-manag
chris    pts/0    :0.0             19:23    0.00s  0.12s  0.00s w
```

so to get how many seconds the X process is idle... I can do

```
$ w | grep x-session-manag | awk {'print $5'} | cut -c1
0

```

---

### Post by ghostdog74 on 2008-08-28
no need to be so tedious
```

w |  awk '/x-session-manage/{print substr($5,1,1)}'

```

---

### Post by cbdonohue on 2008-08-28
That doesn't work for me...and doesn't help solve the problem

---

### Post by ghostdog74 on 2008-08-28
> **cbdonohue said:**
> That doesn't work for me...and doesn't help solve the problem
that should be equivalent to your grep/cut/awk combination. anyway, that doesn't matter now since you solved the problem.

---


---
title: "Batch &amp; load"
date: 2005-10-08
forum: Programming Talk
---

### Post by tlanglois on 2005-10-08
Hello,

The batch command allows a program to run later when the load of the machine is below a given level.  On fedora the threshold is 0.8 (see man batch) on Ubuntu it is 1.x (i do not have my ubuntu compter with me i don't what x is)

The problem is that I want to run some programs (that run for a long time and use a lot of cpu and memory ressources) one at a time. If the threshold is set to 0.8 like on fedora, it is fine. If it is > 1 then two programs run at the same time. So the question is : 
How can I change this threshold value ?  

I hope it will not be necessary to recompile anything :-/

Thibault Langlois

---

### Post by six6 on 2005-10-08
Edit the /usr/sbin/atrun (a shell script); change the line 
```
exec ${exec_prefix}/sbin/atd -s "$@"
``` to ```
${exec_prefix}/sbin/atd -s "$@" -l <new load value>
```that should fix it.

---

### Post by tlanglois on 2005-10-08
[QUOTE=six6]Edit the /usr/sbin/atrun (a shell script); change the line 
```
exec ${exec_prefix}/sbin/atd -s "$@"
``` to ```
${exec_prefix}/sbin/atd -s "$@" -l <new load value>
```that should fix it.[/QUOTE]
Thank you, I will try.

Thibault

---

### Post by six6 on 2005-10-09
Whoops, forgot that the last line should read
```
**exec** ${exec_prefix}/sbin/atd -s "$@" -l <new load value>
```

---

### Post by tlanglois on 2005-10-10
Well, it did not work. It seems that /usr/sbin/atrun is not used. 

I aparently solved the problem editing /etc/init.d/atd and changing:

ARGS=""

to

ARGS="-l 0.8"

Thank you for your help, you gave me the idea.

Thibault

---


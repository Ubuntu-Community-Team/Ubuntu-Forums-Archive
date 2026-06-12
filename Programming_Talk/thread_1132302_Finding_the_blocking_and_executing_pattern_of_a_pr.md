---
title: "Finding the blocking and executing pattern of a process"
date: 2009-04-21
forum: Programming Talk
---

### Post by DrFugly on 2009-04-21
So I've just been assigned a project. (Yes I specifically asked if I can use forums for help and I was given the nod) 

I need to be able to track how long a process runs for, then sleeps, then runs and so on... basically along the lines finding data like:
```
Firefox:
Executes for 5 seconds
Blocks for 20 seconds
Executes for 6 seconds
Blocks for 15 seconds

and so on...
```

so my first attack was to keep polling /proc/{pid}/status to see what was going on ie: ```
`cat /proc/3831/status | grep State`
```. And maybe doing that a lot to get a picture. But of course I just keep on getting that all of my procs are sleeping.

So now I'm thinking of modifying the kernel's scheduler to keep track of which tasks its allowing to run. 

I caught a glimpse of the following:
[http://lxr.linux.no/linux+v2.6.29/include/linux/sched.h#L209](http://lxr.linux.no/linux+v2.6.29/include/linux/sched.h#L209)

a function called "set_task_state" is defined.

Does anyone know if this is the common method used to actually set a task_state? Is this valid way to gain access to the data that I need? Is there an easier way?

Thank you all!

---

### Post by eskimo88 on 2009-04-23
try this link:

[http://docs.cs.up.ac.za/programming/asm/derick_tut/syscalls.html](http://docs.cs.up.ac.za/programming/asm/derick_tut/syscalls.html)

it helped me in a similar situation

---


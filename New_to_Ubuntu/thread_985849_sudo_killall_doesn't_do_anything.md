---
title: "sudo killall doesn't do anything"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by shmish on 2008-11-18
I've been unable to kill processes by using either kill or killall.  I tried sudo kill pid, sudo killall processname, tried using the Gnome System Monitor.  Nothing seems to actually kill the processes and I really don't know why...

thanks

---

### Post by nhasian on 2008-11-18
from a terminal:
you can use *xkill* and then click on the application you want to end if it has a gui.  also you can use *top* to display running applications, then press *k* to kill a process by entering its PID.

---

### Post by ja660k on 2008-11-18
or you can use 

```

killall -v x

```

where x is the name of the program you wish to kill

---

### Post by bodhi.zazen on 2008-11-18
> **shmish said:**
> I've been unable to kill processes by using either kill or killall.  I tried sudo kill pid, sudo killall processname, tried using the Gnome System Monitor.  Nothing seems to actually kill the processes and I really don't know why...

thanks

sometimes you need to use -9 or -1

sudo killall -1 foo
suod killall -9 foo

---


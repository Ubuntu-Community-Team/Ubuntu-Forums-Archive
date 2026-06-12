---
title: "a question for the people..."
date: 2008-05-05
forum: New to Ubuntu
---

### Post by fignig on 2008-05-05
is there some kind of application/program that resembles the work of "task manager" where you can see all of the other running apps and manipulate/stop them. anyone know what i'm talking about?

---

### Post by PeterJS on 2008-05-05
Yep, Gnome system monitor, it can be found at System > Administration > System Monitor.

---

### Post by SunnyRabbiera on 2008-05-05
yes, its called the system monitor, its under system in administration listed as system monitor.
with this app you can view system information, processes (task manager), resources (memory and junk) and file systems.

---

### Post by cartisdm on 2008-05-05
Also you can use Force Quit to shutdown any problems or frozen windows if that's your intention of the task manager

---

### Post by tw3k on 2008-05-05
> **fignig said:**
> is there some kind of application/program that resembles the work of "task manager" where you can see all of the other running apps and manipulate/stop them. anyone know what i'm talking about?

I don't know if there is is a graphical application that resembles Task Manager.

I would, however, suggest the command line program "top."

three informative commands:

man top
man kill
man killall

---

### Post by subzero316 on 2008-05-06
try command

```
ps
```

---

### Post by tw3k on 2008-05-06
> **subzero316 said:**
> try command

```
ps
```

Good one! Funny how you use things and don't even think about it.

---

### Post by fignig on 2008-05-06
> **tw3k said:**
> Good one! Funny how you use things and don't even think about it.

  PID TTY          TIME CMD
26474 pts/1    00:00:00 bash
26501 pts/1    00:00:00 ps


wat exactly is this?

---

### Post by hyper_ch on 2008-05-06
htop

```

sudo apt-get install htop

```

```

htop

```

---

### Post by erginemr on 2008-05-06
+1 for **htop**

---

### Post by subzero316 on 2008-05-06
```

ps -a
```

ps lists the processes
To learn about ps 

```
man ps
```

---

### Post by Michael.Godawski on 2008-05-06
> PID TTY TIME CMD
26474 pts/1 00:00:00 bash
26501 pts/1 00:00:00 ps


what exactly is this?

[http://www.ocf.berkeley.edu/sysadmin-class/2002-spring/2002-04-10.html](http://www.ocf.berkeley.edu/sysadmin-class/2002-spring/2002-04-10.html)

---

### Post by inportb on 2008-05-06
KSysGuard ftw? Press ^ESC in KDE =p

---


---
title: "[SOLVED] Bash command to display CPU load?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-18
Hi, all:

Is there a bash command to display the percentage of cpu being used?  I have a C2D, and I can't find any command to display the percentage of use on both of them.

---

### Post by hyper_ch on 2008-11-18
how about running "top"?
Although I prefer "htop" which you first have to install.

---

### Post by iponeverything on 2008-11-18
```
uptime
```

---

### Post by ByteJuggler on 2008-11-18
There's "top", which is interactive, then there's "uptime", "who" and "procinfo" (the latter which you'll likely have to install first.)

The load averages they report are system load averages for the last 1, 5 and 15 minutes respectively.  The way I like to think of this (which is probably an over simplification in some way, but it works well enough for me) is that a load average of 1 means there's enough work being done by the system to keep 1 cpu busy 100% of the time.  (So either 1 process taking 100% or 2 processes taking each 50% etc.)  A load average of 2 would likewise be enough to consume 100% of 2 cpu's.  Etc.

---

### Post by tarahmarie on 2008-11-18
~/Documents/Scripts : Yes, Supreme Empress? $ uptime
 03:27:23 up  2:43,  2 users,  load average: 0.53, 0.52, 0.52


So, how do I interpret this?  Meaning: which one's the first core, which one is the second, and why does it say there are 2 users?  Does that mean root and me?

---

### Post by scorp123 on 2008-11-18
> **tarahmarie said:**
> So, how do I interpret this? Read the manual, it's all there: ```
man uptime
``` (press "Q" to quit the manual again)

As for your other question: If you were logged in twice then this too counts as "2 users". And being logged in twice could mean e.g. being logged into GNOME plus having a terminal open. Check with the "w" or "who" command, this should print out who's logged in. Chances are you will see yourself twice: 
```
> w
 12:42:18 up  3:44,  2 users,  load average: 0.22, 0.25, 0.19
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
sysadm      tty7     :0               08:59    0.00s  4:09m  0.50s /usr/bin/gnome-session
sysadm      pts/1    :0.0             11:56    0.00s  0.16s  0.01s w
``` There you go ... tty7 is GNOME, the other session is an open terminal. Hence: "2 users".

---

### Post by iponeverything on 2008-11-18
> **tarahmarie said:**
> ~/Documents/Scripts : Yes, Supreme Empress? $ uptime
 03:27:23 up  2:43,  2 users,  load average: 0.53, 0.52, 0.52


So, how do I interpret this?  Meaning: which one's the first core, which one is the second, and why does it say there are 2 users?  Does that mean root and me?

Uptime, Supreme Highness, does not break down by core.  His eminence,  ByteJuggler, explains it very well in his post. I, the Jester and loyal servant, will demonstrate by juggling some processes. ;)

---

### Post by tarahmarie on 2008-11-18
@iponeverything:

You are given my permission to juggle processes.

Thanks, all, for the explanations!

---

### Post by light50 on 2009-06-28
From ```
man uptime
```
> DESCRIPTION
uptime gives a one line display of the following information.  The current time, how long the system has been running,  how  many  users  are currently  logged  on,  and the system load averages for the past 1, 5, and 15 minutes

---


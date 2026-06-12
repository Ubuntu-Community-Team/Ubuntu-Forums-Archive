---
title: "[SOLVED] 2 of the same login"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Xoanan on 2008-06-27
Hi All

I am not sure why, but while looking around the system, I found that 2 users are active on my system -- both of them are me.  I rebooted the system and logged in, and it is still the same.  I don't know if this is covered in the docs, so could someone take a look?

```
xoanan@ubuntu:~$ uptime
 04:42:42 up  6:32,  2 users,  load average: 0.07, 0.15, 0.14
xoanan@ubuntu:~$ users
xoanan xoanan
xoanan@ubuntu:~$ w
 04:43:29 up  6:32,  2 users,  load average: 0.03, 0.13, 0.13
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
xoanan   tty7     :0               04:32    0.00s 46.46s  0.02s /bin/sh /etc/xd
xoanan   pts/0    :0.0             04:42    0.00s  0.34s  0.00s w
xoanan@ubuntu:~$ who
xoanan   tty7         2008-06-27 04:32 (:0)
xoanan   pts/0        2008-06-27 04:42 (:0.0)
xoanan@ubuntu:~$ 

```


:popcorn:

---

### Post by Elfy on 2008-06-27
Can't remember the reason as it was a while back I saw similar - but it's normal afaik

> kevin@kevin-desktop:~$ uptime
 11:25:55 up 30 min,  2 users,  load average: 0.83, 0.51, 0.39
kevin@kevin-desktop:~$ users
kevin kevin
kevin@kevin-desktop:~$ w
 11:26:53 up 31 min,  2 users,  load average: 0.65, 0.51, 0.39
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
kevin    tty7     :0               10:55    0.00s  1:29m  0.20s /usr/bin/gnome-
kevin    pts/0    :0.0             11:25    0.00s  0.18s  0.00s w
kevin@kevin-desktop:~$ who
kevin    tty7         2008-06-27 10:55 (:0)
kevin    pts/0        2008-06-27 11:25 (:0.0)
kevin@kevin-desktop:~$ 

---

### Post by mcduck on 2008-06-27
Each teminal you have open counts as a new user being logged in. (yes, same yuser can log in to Linux multiple times, and from multiple locations.)

So, if you see 2 users, one is you logged in to the desktop, and the other is you logged in to that terminal.

---

### Post by Xoanan on 2008-06-27
Thanx all!

Xoanan

---

### Post by Elfy on 2008-06-27
welcome - could you mark thread solved as well please :D

---

### Post by Xoanan on 2008-06-27
Done;  thanx!

---


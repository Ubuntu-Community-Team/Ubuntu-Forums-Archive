---
title: "Mu user name repeats five times?"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-02-23
Why does users show one name five times?

mark@Lexington-19:~$ users
mark mark mark mark mark

---

### Post by Bucky Ball on 2013-02-23
Perhaps you have five users named mark. Have a look in Users & Groups and see what's in there. If you have one user setup, that should show one user; mark. You might have different permissions for your five but it does sound strange. 

When you get to the login screen do you have the option to login as one of the five marks or is only one showing?

---

### Post by steeldriver on 2013-02-23
it reports each tty / pts separately I think - you can use the 'who' and/or 'w' commands for more details e.g.

```
$ users
steeldriver steeldriver steeldriver
$
$ who
steeldriver  tty7         2013-02-20 08:37
steeldriver  pts/1        2013-02-20 09:07 (:0.0)
steeldriver  pts/3        2013-02-23 22:20 (192.168.1.5)
$
$ w
 22:21:11 up 3 days, 13:44,  3 users,  load average: 0.06, 0.09, 0.12
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
steeldriver  tty7                      Wed08    3days  3:16m  0.66s gnome-session -
steeldriver  pts/1    :0.0             Wed09    8:31   2.59s  2.59s bash
steeldriver  pts/3    192.168.1.5      22:20    0.00s  0.47s  0.00s w
$

```

---

### Post by deadflowr on 2013-02-23
How many terminals do you have open?
Either ttys or pts'.
Every terminal session opened by you adds another you.
By default, you should always have one, and when you open a single terminal it'll show two, and if a third terminal is opened it'll show three, and so on.
You can run the w command to see what's open.

---

### Post by Mark_in_Hollywood on 2013-02-24
That was it. I had a terminal open with 3 or 4 tabs, one running top, another iotop, a third ...

Currently:

mark@Lexington-19:~$ who
mark     tty7         2013-02-24 08:53
mark     pts/2        2013-02-24 08:54 (:0.0)
mark     pts/0        2013-02-24 08:55 (:0.0)
mark     pts/4        2013-02-24 10:09 (:0.0)


mark@Lexington-19:~$ users
mark mark mark mark

all a-ok.

thank you.

---


---
title: "running who in terminal"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by elsteamola on 2012-08-01
Hi All:

running 'who' in a terminal yields:

gh       tty7         2012-08-01 06:00
gh       pts/0        2012-08-01 19:50 (:0)
 
running  ps aux | less to search for tty7 yields:

root      3755  2.8  1.2  32120 16240 tty7     Ss+  00:39  33:07 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch

My very humble urgent question:
do I have a security issue?
why is tty7 logged in?

All relevant help greatly appreciated.

elsteamola

---

### Post by audiomick on 2012-08-01
my results

```
mick@mick-laptop:~$ who
mick     tty7         2012-08-02 01:49 (:0)
mick     pts/0        2012-08-02 02:11 (:0.0)
mick     pts/1        2012-08-02 02:34 (:0.0)


```

I don't know the in's and out's of it. Maybe someone will come along who can explain in detail. Any rate, you don't have a security problem. There are always a couple of "extras" logged on. That is just the system doing it's business.

---

### Post by papibe on 2012-08-01
Hi elsteamola.

It's normal. TTY7 is where your graphical session is held, thus where 'X' is running.

Take a look at this explanation on Linux and Ubuntu's use of ttys: [Working with TTY sessions]("http://mostlylinux.wordpress.com/troubleshooting/ttysessions/").

Tell us how it goes.
Regards.

---

### Post by elsteamola on 2012-08-01
Thanks all.

Yup.  Got 7 tty processes.

---

### Post by papibe on 2012-08-01
:D

Please mark this thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---


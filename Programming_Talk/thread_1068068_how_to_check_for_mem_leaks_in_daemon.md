---
title: "how to check for mem leaks in daemon"
date: 2009-02-12
forum: Programming Talk
---

### Post by monkeyking on 2009-02-12
Hey, I'm writing a unix daemon.


But I would like to check if it leaks memory.
Normally I would use, valgrind,
but this wont really do any good.

Since the daemon is supposed to run forever.

any advice?
Should I just run it for a day or so,
and then check how much mem it uses?

thanks in advance

---

### Post by Zugzwang on 2009-02-13
Remove the lines making the program a daemon for the time being and end the program at some time. Then you can use valgrind. Daemons normally do not run "forever" but are terminated at some point.

EDIT: A typical termination time is the shutting-down time of the computer.

---

### Post by jimi_hendrix on 2009-02-13
just curious...whats the daemon going to do?

---

### Post by nvteighen on 2009-02-13
> **jimi_hendrix said:**
> just curious...whats the daemon going to do?
Eat your soul :twisted:

---

### Post by jimi_hendrix on 2009-02-13
> **nvteighen said:**
> Eat your soul :twisted:

*grabs shotgun*

---

### Post by Gordon Bennett on 2009-02-13
> **monkeyking said:**
> Hey, I'm writing a unix daemon.


But I would like to check if it leaks memory.
Normally I would use, valgrind,
but this wont really do any good.

Since the daemon is supposed to run forever.

any advice?
Should I just run it for a day or so,
and then check how much mem it uses?

thanks in advance

Similarly, I am writing a daemon that cannot be run as a standalone app because of the 'waiting around' for several conditions to be met by an external process out of its control.

Use mtrace() :)

---

### Post by monkeyking on 2009-02-17
Hi sorry for not getting back on this thread but I had an extended weekend vacation.

@Zugzwang
The daemon is a server app, and we don't reboot our servers to often. Current uptime is 260days. 


> **jimi_hendrix said:**
> just curious...whats the daemon going to do?

I'm rewritting the jmon app that is availble in the repos.
It's a distributed network usage monitor for terminal use.
It's written in with ncurses. The original program is written by some guy called jaco but hasn't been updated since 1999, and is orphaned.
Below is a screenshot.

[[IMG]http://img291.imageshack.us/img291/1808/tmonyx4.jpg[/IMG]](http://img291.imageshack.us/my.php?image=tmonyx4.jpg)
[[IMG]http://img291.imageshack.us/img291/tmonyx4.jpg/1/w523.png[/IMG]](http://g.imageshack.us/img291/tmonyx4.jpg/1/)
The program is up and running,
I've updated the threading model, made the connection more robust, and changed the swap monitor to a harddisk monitor.


@gordon
thanks I've never heard of mtrace, looks very usefull.

---


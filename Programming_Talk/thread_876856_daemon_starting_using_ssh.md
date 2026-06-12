---
title: "daemon starting using ssh"
date: 2008-08-01
forum: Programming Talk
---

### Post by techno.naru on 2008-08-01
hello friends 

i am trying to start the drqueue-slave daemon using ssh
but the problem is that the command
ssh [email]root@10.0.1.xxx[/email] /etc/init.d/drqueue-slave restart

the command executes without error but the daemon does not start

but if i manually go to the machine using ssh and then execute the command the daemon starts....

what shall i do...

---

### Post by Spudster on 2009-08-28
Any ideas on this?  I have the same problem.

---

### Post by dribeas on 2009-08-30
Looks as if the environment is different. Try executing with some extra information, something as:

ssh root@host sh -x /etc/init.d/script

With some luck you will get some extra information on what is really going on there.

---


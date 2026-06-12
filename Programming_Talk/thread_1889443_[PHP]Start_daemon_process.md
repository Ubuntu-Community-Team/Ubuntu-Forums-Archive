---
title: "[PHP]Start daemon process"
date: 2011-12-01
forum: Programming Talk
---

### Post by Dave002 on 2011-12-01
Hi guys,

I've been trying to execute an external  program as a daemon from PHP for a while and I did nearly no progress.
I donwloaded the 'daemon' package using the command: apt-get install daemon.

Here's what i have so far:
[PHP]shell_exec("daemon -D /opt/lampp/htodcs/site/files /opt/lampp/htdocs/site/files/test");[/PHP]

The executable should generate a logfile when it is started but it doesn't even start so I think there might be a problem with my privileges.I defined 'User' as my username in httpd.conf and I also tried to modify 'Group' to root's group but it didn't help.

Regards,
David

---

### Post by Petrolea on 2011-12-01
Are you sure it doesn't start? Maybe it just does nothing and the problem is in code.

And if you're running in safe mode, that command won't work (but I guess that should generate some kind of warning or an error).

---

### Post by Dave002 on 2011-12-02
> **Petrolea said:**
> Are you sure it doesn't start? Maybe it just does nothing and the problem is in code.

And if you're running in safe mode, that command won't work (but I guess that should generate some kind of warning or an error).


Yeah I'm 100% sure. I started the test program from terminal and it is working properly.

---

### Post by Petrolea on 2011-12-02
> **Dave002 said:**
> Yeah I'm 100% sure. I started the test program from terminal and it is working properly.

Do any other simple examples run? Or nothing runs with shell_exec() at all?

Make sure that safe mode is OFF and displaying errors is ON.

You could also try using exec() and see what happens.

---

### Post by Dave002 on 2011-12-02
> **Petrolea said:**
> Do any other simple examples run? Or nothing runs with shell_exec() at all?

Make sure that safe mode is OFF and displaying errors is ON.

You could also try using exec() and see what happens.
I executed the "ls" command and it ran perfectly. I tried exec() as well, got the same result :\

---

### Post by Petrolea on 2011-12-02
Well it must run the daemon command then also. Use exec() and check the output of the command (if there is any). Can't think of nothing better, didn't deal with PHP for long time.

---


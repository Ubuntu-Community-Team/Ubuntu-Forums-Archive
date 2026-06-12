---
title: "Is cp command logged?"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by kenthusiast on 2012-08-14
Hi all,
can anyone please tell me if the cp command is logged anywhere?
I'd like to know if I can go back through the logs and see if a cp
command was performed by any user and what the arguments were.

If so, what logfile is it recorded in?

Also, if a copy is done via a GUI file manager would that also be recorded?

Thanks very much
Ade

---

### Post by unevenflow on 2012-08-14
Hey, you could check .bash_history manually or from terminal for each user e.g. :
```
sudo gedit /home/username/.bash_history
```

---

### Post by kenthusiast on 2012-08-14
> **unevenflow said:**
> Hey, you could check .bash_history manually or from terminal for each user e.g. :
```
sudo gedit /home/username/.bash_history
```

That's true, but users can edit their own and remove a dubious file copy.
I was wondering if syslog could be used to record these in a central log file.

Thanks for your thoughts

Ade

---

### Post by unevenflow on 2012-08-14
ok see this 

[http://askubuntu.com/questions/93566/how-to-log-all-bash-commands-by-all-users-on-a-server](http://askubuntu.com/questions/93566/how-to-log-all-bash-commands-by-all-users-on-a-server)

---

### Post by kenthusiast on 2012-08-14
that's perfect!  Thanks very much indeed.
:-D <-- me right now!

---


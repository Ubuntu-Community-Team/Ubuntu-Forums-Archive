---
title: "APMM - Apache, PHP and MySQL Monitor"
date: 2009-01-23
forum: Programming Talk
---

### Post by coderpp on 2009-01-23
Program main features:
[LIST]
[*]Start/stop/restart all (apache and mysql)
[*]Start/stop/restart apache
[*]Start/stop/restart mysql
[*]Add/remove autostart
[*]See server status - started/stoped, uptime
[*]...
[/LIST]

1. Is there already such program for linux with GUI?
2. How can i start/stop these programs from my program (i will write in c++)?
3. What about user rights? to stop or start apache need super user right.

---

### Post by Reiger on 2009-01-23
(1) Probably. A program to do the start/stop/install stuff is exceedingly easy to make because each action corresponds to a simple command line:
```
sudo /etc/init.d/<service_name> <command>
```
For instance:
```
sudo /etc/init.d/apache2 restart
```
(2) See above.
(3) Yes you will require super-user rights. It ought to be resolved by creating a desktop file (the launcher) which executes (if you want to login as root)
```
gksu <actual_command>
``` or (if you want to login using 'ordinary' sudo)
```
gksudo <actual_command>
```

The <actual_command> is whatever it takes to launch your program. The gksudo or gksu means you'll get a nice GNOME login window first (or fail if you don't have the gk[sudo/su] program) but there is a KDE equivalent as well.

---

### Post by Tibuda on 2009-01-23
For Apache setup you can try ```
[sudo aptitude install rapache]("apt:rapache")
```

---


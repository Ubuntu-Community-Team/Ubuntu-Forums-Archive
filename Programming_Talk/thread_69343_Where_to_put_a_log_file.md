---
title: "Where to put a log file ?"
date: 2005-09-26
forum: Programming Talk
---

### Post by Michele Moglia on 2005-09-26
I wrote an application and I want to add a log file to help
users to catch some problems or send me some informations
about problems.
In which directory do my application write the log file?
I think /var/log/myapp.log but if the user isn't root it doesn't work !
So where /var/log/myapp/myapp.log and change permissions on /var/log/myapp ? But how do this in a debian package ?
Please let me know the right way ?

Thanks

Michele

---

### Post by tageiru on 2005-09-26
It sounds like your application is not a global system service. Only global services are allowed to store logs in /var/log

Put the config file in the users home directory. Preferably under a ".appname" directory (yes the dot is important)

---

### Post by cwaldbieser on 2005-09-26
[QUOTE=tageiru]It sounds like your application is not a global system service. Only global services are allowed to store logs in /var/log

Put the config file in the users home directory. Preferably under a ".appname" directory (yes the dot is important)[/QUOTE]
It would also be nice if you let the user configure where the log file goes via an environment variable or command line option.

---

### Post by LordHunter317 on 2005-09-26
[QUOTE=cwaldbieser]It would also be nice if you let the user configure where the log file goes via an environment variable or command line option.[/QUOTE]Best is to log to the system log spools using syslog() if all at possible, like one is supposed to.

Now, if this isn't a daemon of any sort and it's solely debugging, then just create a debug log file wherever is most convinent -- the important part is that it's not something a user would commonly do.

---


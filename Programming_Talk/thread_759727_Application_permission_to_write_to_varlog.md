---
title: "Application permission to write to /var/log"
date: 2008-04-19
forum: Programming Talk
---

### Post by Asham on 2008-04-19
Quick question: how can I make my application output its log to /var/log?

---

### Post by themusicwave on 2008-04-19
If you are getting a permission denied error try running it as sudo.

If it's a GUI app run it as gksudo <app>

If it's CLI run it as sudo <app>

I think only root has access to that directory.

---

### Post by Asham on 2008-04-19
It is a single-instance of a java servlet that needs to write the log, so it is actually tomcat55 that is the user. Instead of logging into a fake user's home, it'd be better to write the logfile to /var/log. 

Unfortunately, as you suspected, I keep getting permission denied.

Adam

---

### Post by ghostdog74 on 2008-04-19
just change the permission of /var/log to allow tomcat55 user

---

### Post by Asham on 2008-04-20
How would I do that without it affecting the current permissions? 
Sorry but I don't want to potentially mess up other applications.

---

### Post by DMills on 2008-04-20
Don't write to the log directly, instead use the syslog facility that gives you free support for things like remote logging and various log levels.

man syslog for details.

For doing this from the shell, there is a utility called logger. 

man logger for the details of that. 

HTH.

Regards Dan.

---

### Post by Asham on 2008-04-20
> **DMills said:**
> Don't write to the log directly, instead use the syslog facility that gives you free support for things like remote logging and various log levels.

man syslog for details.

For doing this from the shell, there is a utility called logger. 

man logger for the details of that. 

HTH.

Regards Dan.

Sounds great.Thanks for pointing me in the right direction. 
Problem is, syslog is not installed on my computer (I run Kubuntu). "apt-cache search syslog" returned lots of alternatives, which one is it that I need?

---

### Post by mssever on 2008-04-20
> **Asham said:**
> Sounds great.Thanks for pointing me in the right direction. 
Problem is, syslog is not installed on my computer (I run Kubuntu). "apt-cache search syslog" returned lots of alternatives, which one is it that I need?

Have you actually tried it? I don't think that it's possible to have a fully-functional Linux system (any distro) without syslog, since so many programs rely on it. In Ubuntu, it's a required package, and I'd be surprised if that wasn't the case for Kubuntu, as well.

The logger command is part of the bsdutils package. ```
dpkg --search /usr/bin/logger
```

If you have a file named /var/log/syslog, then you have syslog.

---

### Post by ruy_lopez on 2008-04-21
It might be the man page you are missing. Try installing 'manpages-dev', then retrying 'man syslog', which will show the syslog C header information.

---

### Post by Asham on 2008-04-21
I assumed syslog was not installed since I got "no manual for syslog" or something similar when I ran "man syslog".

I followed ruy_lopez advice and now the man command seems to return the information that I need. Thank you both!

---


---
title: "Having problems compiling Squid with SSL and ecap"
date: 2013-06-27
forum: Packaging and Compiling Programs
---

### Post by SteelSlasher on 2013-06-27
Hi,
Im trying to setup a squid proxy for several publicly accessible computers. I have been required to include generation of SSL certificates (--enable-ssl and --enable-ssl-crtd) and also ecap compatibility. I have successfully compiled squid but when i run it from /usr/local/squid/sbin/ i get the following error in the terminal:

Warning: Cannot write log file: /var/log/cache.log
/var/log/cache.log Permission denied
messages will be sent to stderr

The application then quits without any other messages. the cache.log file doesn't exist but creating it doesnt make a difference

I have used the flags from here as well the ones stated above when configuring
[http://wiki.squid-cache.org/KnowledgeBase/Debian#Compiling](http://wiki.squid-cache.org/KnowledgeBase/Debian#Compiling)

---

### Post by Kujua on 2013-06-27
What user are you running squid with? 'proxy'? Perhaps the user does not have write permissions to /var/log/cache.log.

Check the ownership and permissions:
```
ls -l /var/log/cache.log
```

If the file is not owned by the user, change ownership:
```
chown user: /var/log/cache.log
```
Make sure you replace "user" with whatever user you are running squid with.

---


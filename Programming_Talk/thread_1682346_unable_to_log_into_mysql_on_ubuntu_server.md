---
title: "unable to log into mysql on ubuntu server"
date: 2011-02-05
forum: Programming Talk
---

### Post by badperson on 2011-02-05
Hi,
I installed mysql awhile back, but haven't installed any db's yet...I was going to create one today, but when I tried to log into mysql I get an error. 

when I type:
> mysql -r root -p
it prompts me for my password, when I enter it I get: 
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

I tried sudo /etc/init.d/mysql restart

which outputs: 
> $ sudo /etc/init.d/mysql restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mysql
start: Job is already running: mysql


I tried the suggestion in the message and got: 

> $ service mysql restart
restart: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

sudo netstat -tap | grep mysql doesn't output anything...

any ideas?
bp

---


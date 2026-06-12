---
title: "Can anyone help me debug mysql service on Ubuntu desktop? Please"
date: 2015-07-19
forum: New to Ubuntu
---

### Post by TestTestington on 2015-07-19
Hi, I'm pretty new to Ubuntu.

I installed and configured LAMP on Ubuntu 15.04 and everything was working fine for two days until this morning. It seems like mysql just stopped working (no idea why) and I can't get it going again.

```
# pgrep mysql
8865
# mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
# service mysql start
{hangs for a few minutes...}
Job for mysql.service failed. See "systemctl status mysql.service" and "journalctl -xe" for details.
# journalctl -xe
{some other text that seems unrelated then...}
-- Unit mysql.service has begun starting up.
Jul 19 11:33:13 pc mysqld_safe[6525]: 150719 11:33:13 mysqld_safe Can't log to error log and syslog at the same time.  Remove all --log-error configuration options for --syslog to take effect.
Jul 19 11:33:13 pc mysqld_safe[6525]: 150719 11:33:13 mysqld_safe Logging to '/var/log/mysql/error.log'.
Jul 19 11:33:13 pc mysqld_safe[6525]: 150719 11:33:13 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
Jul 19 11:33:16 pc mysqld_safe[6525]: 150719 11:33:16 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended
# service /etc/init.d/mysql start
Failed to start etc-init.d-mysql.service.mount: Unit etc-init.d-mysql.service.mount failed to load: No such file or directory.

```


Please let me know if I can provide any more info to help debug.

---

### Post by TestTestington on 2015-07-19
I managed to solve this myself. I had use a deprecated variable in my.cf. For future reference is there any way that I could have debugged the problem to find out there was an invalid var in my config?

---

### Post by SeijiSensei on 2015-07-19
Was it related to this issue?
```
Jul 19 11:33:13 pc mysqld_safe[6525]: 150719 11:33:13 mysqld_safe Can't log to error log and syslog at the same time.  Remove all --log-error configuration options for --syslog to take effect.
```
If so, then the error message appears to provide all the help you would need.

---


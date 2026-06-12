---
title: "XAMPP mysql problem"
date: 2016-05-05
forum: New to Ubuntu
---

### Post by Jan_Lucas on 2016-05-05
I've just downloaded and installed xampp onto Ubuntu 12.04
it all seemed to go ok, but I don't have the root password for mysql, if I try to log on using phpmyadmin I can't!
how do I either set this password or what is the default?

---

### Post by yancek on 2016-05-05
You have to create a root password for mysql and you should have been prompted to do so during the install.  I guess that depends upon how you installed it.  The mysql root password is NOT the system root password.  Explained at the site below.

 [https://www.howtoforge.com/setting-changing-resetting-mysql-root-passwords](https://www.howtoforge.com/setting-changing-resetting-mysql-root-passwords)

---

### Post by Jan_Lucas on 2016-05-06
Maybe I should explain that I wanted to upgrade, so I uninstalled the old version of xampp and installed the new version (but was not prompted to give a root password). However, the old root password does not work either.
I'll see if I can follow the steps to recover the root password on the link you gave, thanks.

---

### Post by Jan_Lucas on 2016-05-06
in fact the instructions on that page do not work for me... when I enter the command " /etc/init.d/mysql stop" I get the message:

[I]Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql[/I]

so I tried "mysql stop" and "service stop mysql" but neither of those worked.
Then I tried to start using "mysqld_safe --skip-grant-tables &" but that didn't work either - I got the following
[I][1] 31786
janl@oakleighws13:~$ 160506 09:33:57 mysqld_safe Can't log to error log and syslog at the same time.  Remove all --log-error configuration options for --syslog to take effect.
160506 09:33:57 mysqld_safe Logging to '/var/log/mysql/error.log'.
160506 09:33:57 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
/usr/bin/mysqld_safe: 126: /usr/bin/mysqld_safe: cannot create /var/log/mysql/error.log: Permission denied
/usr/bin/mysqld_safe: 1: eval: cannot create /var/log/mysql/error.log: Permission denied
160506 09:33:57 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended
/usr/bin/mysqld_safe: 126: /usr/bin/mysqld_safe: cannot create /var/log/mysql/error.log: Permission denied
[/I]

is there something wrong with my installation?

---

### Post by Jan_Lucas on 2016-05-06
Update: I've also tried this on another PC with a completely fresh installation of Ubuntu and a fresh installation of xampp.
when I type the command "mysqladmin -u root password 1234" I get the message:
"mysqladmin: connect to server at 'localhost' failed
error: can't connect to local MYSQL server through socket '/var/run/mysqld/mysqld.sock"

so I&#8217;m guessing that there must be something wrong with the installation
(I used xampp-linux-5.5.34-0-installer.run)

---

### Post by SeijiSensei on 2016-05-06
That last message indicates that the mysqld server is not running.  Run "sudo service mysql start" and see if that fixes the problem.

---

### Post by Jan_Lucas on 2016-05-07
ok, tried that:
on the old machine I got "start: Job failed to start"
on the fresh install I got "mysql: unrecognized service"

(on both machines the XAMPP control panel shows MySql Database running)

---


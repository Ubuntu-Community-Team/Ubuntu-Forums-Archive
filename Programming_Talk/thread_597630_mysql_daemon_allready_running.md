---
title: "mysql daemon allready running"
date: 2007-10-30
forum: Programming Talk
---

### Post by FnTm on 2007-10-30
So here we go.

I have a pc with Gusty on it, and I installed XAMPP on it, so i could make my webpages with ease. Im kinda newbie, so i started installing all sorts of things, and now ive run into some problems. I try to start my webserver:

fntm@fntm-ubuntu:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

and it wont start mysql, no matter what i do. Som now im trying to find out whats taking my database.

Any help finding out, what program does this to me? Any commands?

Edit:

Did some commands on it, and got this reply, hope its helpfull:

fntm@fntm-ubuntu:~$ ps -aux | grep 'mysql'
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root      5466  0.0  0.0   1752   528 ?        S    19:43   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     5520  0.0  0.7 126920 16128 ?        Sl   19:43   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5521  0.0  0.0   1676   548 ?        S    19:43   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
fntm      9535  0.2  0.9  35516 19940 ?        S    23:04   0:02 gedit file:///usr/share/mysql/mysql-test/mysql-test-run
fntm     10241  0.0  0.0   2184   772 pts/0    S+   23:18   0:00 grep mysql

---

### Post by dataw0lf on 2007-10-30
XAMPP comes packaged with it's own MySQL server.  You have one already taking up the port.

Run:

```
sudo /etc/init.d/mysql stop
```

it might be sudo /etc/init.d/mysqld stop, actually.

Can you tell I don't use MySQL? ;-)

Cheers.

---

### Post by FnTm on 2007-10-30
Thanks, worked like a charm! :D

---

### Post by dataw0lf on 2007-10-30
:)  Good to know.  Good luck!

---

### Post by edu77pose on 2009-07-20
Thanks for that code, it helped me as well!

---

### Post by thelevogyre on 2009-10-05
It worked for me too. But what can be the cause of this? so that  I don't need to paste this code every time I want to run LAMPP...
thanks

---

### Post by opigss on 2009-12-20
Yea, this helped me too... good code.
ty

---

### Post by tripwire45 on 2010-02-18
I'll just add my thanks, too. Had issues with both MySQL and Apache. Fixed now.

---

### Post by boulbo on 2011-08-31
thanks, it helps me a lot :popcorn:

---


---
title: "Install MySQL 4.x on Ubuntu 12.04"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by rafaelvidal on 2013-02-09
Hello,

I use Ubuntu 12.04 and my application requires old version of MySQL server (4.x to be more precise).

Since I am not sure if I am doing the right, I will describe what I have tried so far to give you an image of what is going on.

[SIZE="3"]What I have done so far?[/SIZE]

**DOWNLOADED** "MySQL-4.1/MySQL-server-4.1.21-0.glibc23.x86_64.rpm" from [mysql.mirror.kangaroot.net/pub/mysql/Downloads/MySQL-4.1/]("ftp://mysql.mirror.kangaroot.net/pub/mysql/Downloads/MySQL-4.1/")

**INSTALLED** "Alien" to convert "rpm" into "deb" and runned dpkg to try to install it.

[SIZE="3"]ERRORS:[/SIZE]
```
**rafael:/home#**dpkg -i mysql-server_4.1.21-1_amd64.deb
(Reading database ... 55062 files and directories currently installed.)
Unpacking mysql-server (from mysql-server_4.1.21-1_amd64.deb) ...
dpkg: error processing mysql-server_4.1.21-1_amd64.deb (--install):
 trying to overwrite '/usr/bin/myisam_ftdump', which is also in package mysql-client-5.5 5.5.29-0ubuntu0.12.04.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Errors were encountered while processing:
 mysql-server_4.1.21-1_amd64.deb
```


That's it...any clues?

---

### Post by SeijiSensei on 2013-02-09
Your best bet is to [build it from source]("https://help.ubuntu.com/community/CompilingEasyHowTo") after installing the build-essential package.

That said, what kind of application "requires" MySQL 4.x?  Will it simply not talk to a MySQL 5.x server, or is it a problem with transferring the data from an old to a new machine?  The solution to that is to write a plain-text file with mysqldump and read it into a 5.x server with the mysql command-line client.

---

### Post by CharlesA on 2013-02-09
> **SeijiSensei said:**
> Your best bet is to [build it from source]("https://help.ubuntu.com/community/CompilingEasyHowTo") after installing the build-essential package.

+1. The only reason to use alien if when there isn't a source package available. Building from source is usually a better idea.

> That said, what kind of application "requires" MySQL 4.x?  Will it simply not talk to a MySQL 5.x server, or is it a problem with transferring the data from an old to a new machine?  The solution to that is to write a plain-text file with mysqldump and read it into a 5.x server with the mysql command-line client.

Agreed. I've not run into anything that wouldn't work on MySQL 5. Even the wiki we have at work, which was running on an ancient version of MySQL imported ok into the newer version of MySQL.

---

### Post by rafaelvidal on 2013-02-09
> **SeijiSensei said:**
> Your best bet is to [build it from source]("https://help.ubuntu.com/community/CompilingEasyHowTo") after installing the build-essential package.

That said, what kind of application "requires" MySQL 4.x?  Will it simply not talk to a MySQL 5.x server, or is it a problem with transferring the data from an old to a new machine?  The solution to that is to write a plain-text file with mysqldump and read it into a 5.x server with the mysql command-line client.

My application uses reserved words and didn't escape them...that's why...

Thank you for your hint.
I managed to do that and now it's working.


CharlesA, I appreciate your attention too.

---


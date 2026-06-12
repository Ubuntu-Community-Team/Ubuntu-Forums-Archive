---
title: "how to determine where mysql files are stored on filesytem"
date: 2011-03-25
forum: Programming Talk
---

### Post by badperson on 2011-03-25
Hi,
I installed mysql on my home server, not from the repo but from the mysql download site. I installed the amd 64 x86 version 5.5.9-2. 

I have a large HD I want to use for the database...when I've done this before I've just changed the path in my.cnf. But now I'm not sure which to change. I have multiple conf files: 

```
$ sudo find / -name "my*.c*"
/var/lib/dpkg/info/mysql-server.conffiles
/media/share/mysqlDownload/MySQL-test-5.5.9/usr/share/mysql-test/suite/federated/my.cnf
/media/share/mysqlDownload/MySQL-test-5.5.9/usr/share/mysql-test/suite/rpl/my.cnf
/usr/share/doc/MySQL-server-5.5.9/my-large.cnf.gz
/usr/share/doc/MySQL-server-5.5.9/my-huge.cnf.gz
/usr/share/doc/MySQL-server-5.5.9/my-innodb-heavy-4G.cnf.gz
/usr/share/doc/MySQL-server-5.5.9/my-medium.cnf.gz
/usr/share/doc/MySQL-server-5.5.9/my-small.cnf
/usr/share/mysql/my-medium.cnf
/usr/share/mysql/my-large.cnf
/usr/share/mysql/my-innodb-heavy-4G.cnf
/usr/share/mysql/my-huge.cnf
/usr/share/mysql/my-small.cnf
/usr/bin/mysqlaccess.conf

```

all of the cnf files, like my-medium.cnf have this line in them:
> # Uncomment the following if you are using InnoDB tables
#innodb_data_home_dir = /var/lib/mysql


Can I just use regular tables? Where would I edit the *.cnf file for that? 
thanks, 
bp

---

### Post by Some Penguin on 2011-03-26
Did you actually run mysql_install_db ?

---

### Post by dazman19 on 2011-03-26
are you looking for the data? Or just for the install files.

Depending on what db-engine you are running will determine what the data files will be called. ibdata1 is generally your innodb file.

MyISAM makes multiple files, i cant remember their extensions .TMD maybe i cant remember, i dont use myISAM but googling it should reveal the answer. 

Personaly I prefer InnoDB as I like transaction and FK constraints. MyISAM is better for speed and full text searching but not very nice in a giant application.

---


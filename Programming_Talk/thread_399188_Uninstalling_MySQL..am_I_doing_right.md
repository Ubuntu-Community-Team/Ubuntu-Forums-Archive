---
title: "Uninstalling MySQL..am I doing right?"
date: 2007-04-02
forum: Programming Talk
---

### Post by HighD on 2007-04-02
Ok, so I installed MySQL from **mysql-5.1.15-beta-linux-i686-glibc23.tar.gz** file I downloaded from their MySQL.com , following this instructions basically...


```

shell> groupadd mysql
     shell> useradd -g mysql mysql
     shell> cd /usr/local
     shell> gunzip < /PATH/TO/MYSQL-VERSION-OS.tar.gz | tar xvf -
     shell> ln -s FULL-PATH-TO-MYSQL-VERSION-OS mysql
     shell> cd mysql
     shell> scripts/mysql_install_db --user=mysql
     shell> chown -R root  .
     shell> chown -R mysql data
     shell> chgrp -R mysql .
     shell> bin/mysqld_safe --user=mysql &
```

How do I uninstall? My idea is to simply trace back my steps and undo what I did. Am I doing right?

Thanks in advance for your help :)

---

### Post by HighD on 2007-04-02
anyone?? I just want to know if retracing my steps would be wise :)

---

### Post by lnostdal on 2007-04-02
the steps for uninstalling mysql from the terminal is as follows:

```
sudo aptitude remove mysql-server
```

..that's assuming you installed it like this:

```
sudo aptitude install mysql-server
```

is there some reason you downloaded and installed the package from some "random web page" instead of using the ubuntu repositories (apt-get / aptitude / synaptic)?

---

### Post by HighD on 2007-04-02
> **lnostdal said:**
> 
is there some reason you downloaded and installed the package from some "random web page" instead of using the ubuntu repositories (apt-get / aptitude / synaptic)?

Thanks lnostdal :D

Well yes there is a reason, I'm a student taking a db course for the first time. I was specifically told to install MySQL 5.1 (even though it's beta). I downloaded the file from [http://dev.mysql.com/downloads/mysql/5.1.html]("http://dev.mysql.com/downloads/mysql/5.1.html") and followed the instructions I posted earlier.

When I do a search in synaptic, it does not show MySQL 5.1 as installed either. but that makes sense as I didn't use a deb file right? I did not do any make or make install, i just followed the above instructions.

---

### Post by HighD on 2007-04-03
Well, what i ended up doing was retracing steps, everything seems to be fine :D

---


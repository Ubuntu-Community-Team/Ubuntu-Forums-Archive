---
title: "Trouble with mysql installation on Ubuntu"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Bucephalus01 on 2008-08-28
When I read the Post-installation procedure in the MYSQL manual it says to do this:
"shell>bin/mysqld_safe --user=mysql &"

So I do that and I get this:
david@Magnus:~$ /usr/bin/mysqld_safe --user=mysql &
[1] 6368
david@Magnus:~$ nohup: ignoring input and redirecting stderr to stdout
cat: /var/run/mysqld/mysqld.pid: Permission denied
rm: cannot remove `/var/run/mysqld/mysqld.pid': Permission denied
mysqld_safe[6410]: Fatal error: Can't remove the pid file: /var/run/mysqld/mysqld.pid
mysqld_safe[6412]: Please remove it manually and start /usr/bin/mysqld_safe again
mysqld_safe[6414]: mysqld daemon not started


I am new to Ubuntu and new to mysql. I have put this in the mysql forums with no response. Does anyone know why I can't get this command to work?

Regards
David

---

### Post by eightmillion on 2008-08-28
You need to be root.
> sudo /usr/bin/mysqld_safe --user=mysql &

---

### Post by Bucephalus01 on 2008-08-28
OF course....thanks for your help.
Ubuntu forums rule.

---

### Post by howlingmadhowie on 2008-08-28
you shouldn't need to use this function. if you installed mysql from the repositories, the server will start automatically. you can stop and start it manually using /etc/init.d/mysql:
```

sudo /etc/init.d/mysql stop
```

will stop the mysql server
```

sudo /etc/init.d/mysql start
```

will start it.

if you installed mysql-server from the repositories, you should have been asked for a password for the mysql administrator. you will need this to add new users and databases to the mysql installation.

---

### Post by Bucephalus01 on 2008-08-28
Thanks for that extra information.
I did install it from the repositories and it did ask me for a password for my root user account. I tried those two commands you recommended and they are working also, I think. How would I test that the server has started automatically or that the commands you gave me did work?

Would this command test it?
/usr/bin/mysql -e "SELECT Host, Db, User FROM db" mysql

THis is a command out of the mysql manual in the post installation section.
I'm going to restart now and see if I can execute this command. I will bring this forum up on my windows computer.

thanks for your time.

---

### Post by unca.paka on 2008-08-28
A quick, 
```
sudo /etc/init.d/mysql status
```
should show the server status(running/stopped)
Pretty sure, by default, the server will start automatically on every startup(it does for me at least).

---

### Post by Bucephalus01 on 2008-08-28
Well I executed that command I was going to execute and it worked.
Also I did the status command that you suggested and it has a variable called "uptime": it changes, i.e. is greater every time I run that command, so I would say that that means the server has been up and running for that time.

thanks for your help.
David

---

### Post by howlingmadhowie on 2008-08-28
you can start a mysql shell session by entering:

```
mysql -u root -p
```

it will ask for the password you configured. then you can see the databases and tables running on your computer.

---


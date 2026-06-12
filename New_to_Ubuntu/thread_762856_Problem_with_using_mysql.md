---
title: "Problem with using mysql"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by linuxneeewb on 2008-04-22
I recently installed mysql using the following url:
[http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/)

And I simply used the following commands:
sudo apt-get install mysql-server
sudo apt-get install php5-mysql

I used the official mysql tutorials to try to figure out how to start using it, but I simply don't know how to start using it. 
I used to following url to get me started.
[http://dev.mysql.com/doc/refman/5.0/en/connecting-disconnecting.html](http://dev.mysql.com/doc/refman/5.0/en/connecting-disconnecting.html)

It gives me the command
mysql -h host -u user -p

My problem is, I have installed mysql on my own Ubuntu computer, but I can't figure out for life of me, what my hostname is. I have tried my user name which is root, and many other combinations.

I know the SQL language, I just need to know how to actually use mysql on my own computer, and how to log into it. Any and all help is appreciated.

Thank You

:lolflag:

---

### Post by Dr Small on 2008-04-22
Hostname???

Um, user@hostname.
Or, type:
```
hostname
```

---

### Post by Can+~ on 2008-04-22
user: root
password: the one you set up on the install.
host: localhost or 127.0.0.1 or even the name of your computer.

If you ignore the -h flag, then it will assume it's local host.

And if you want a fancier UI, you can install mysql-admin, which adds a shortcut on Applications>Programming with the mysql admin client.

Host is used when you're connecting a remote server.

---

### Post by linuxneeewb on 2008-04-22
I have typed hostname command and gotten my hostname.

when I type: 
mysql -h myhostname -u myusername -p 
I get the error
Can't connect to MySQL server on myhostname.

I know that I typed my password correct, my username is correct, and so forth.

When I tried doing just
mysql -u myusername -p
I get the error:
Access denied for user 'username'@'localhost' (using password: YES)

---

### Post by Can+~ on 2008-04-22
again, username = root

not your username, not the root of the system, is the root on the mysql, the first account created by default on install.

Example:

> mysql -u root -p
password: <invisible characters>

---

### Post by linuxneeewb on 2008-04-22
Thanks a lot Can+~. It works perfectly now. 

:KS
:guitar:

---


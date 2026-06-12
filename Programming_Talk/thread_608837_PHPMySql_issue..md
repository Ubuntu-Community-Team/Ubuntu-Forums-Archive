---
title: "PHP/MySql issue."
date: 2007-11-10
forum: Programming Talk
---

### Post by Kadrus on 2007-11-10
Each time I try to connect and work with a data in a database..I get an error..

Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Can someone help me fix this,please?

---

### Post by carlosjuero on 2007-11-10
is mysql running? (Don't take that the wrong way, I ran across the same thing after doing a LAMP install.. apparently though I forgot to actually do a full install of MySQL).

Type mysql at the terminal prompt and see what it says, if it enters into the mysql command line then double check to make sure that you are providing the proper host name.

Edit: also make sure that the server is set to allow your host to connect

---

### Post by Kadrus on 2007-11-10
> **carlosjuero said:**
> is mysql running? (Don't take that the wrong way, I ran across the same thing after doing a LAMP install.. apparently though I forgot to actually do a full install of MySQL).

Type mysql at the terminal prompt and see what it says, if it enters into the mysql command line then double check to make sure that you are providing the proper host name.

Edit: also make sure that the server is set to allow your host to connect
When I type MySql in Terminal I get
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by aks44 on 2007-11-10
What does 

```
sudo /etc/init.d/mysql start
```
say?


If it started your MySQL server, can you connect now?

---

### Post by Kadrus on 2007-11-10
> **aks44 said:**
> What does 

```
sudo /etc/init.d/mysql start
```
say?


If it started your MySQL server, can you connect now?
It tells me 
Starting MySQL database server mysqld..
and then after a sec or 2..i get [failed]..

---

### Post by aks44 on 2007-11-10
Ouch.

How come so many people seem to have trouble installing MySQL these days? :(

Unfortunately I don't have the knowledge to troubleshoot this kind of problems.

My best advice would be to **apt-get remove --purge** mysql (and apache / php / phpmyadmin if you installed them) then use the **tasksel** utility and select the LAMP stack. This will take care of (almost) everything for you.

---

### Post by Kadrus on 2007-11-10
> **aks44 said:**
> Ouch.

How come so many people seem to have trouble installing MySQL these days? :(

Unfortunately I don't have the knowledge to troubleshoot this kind of problems.

My best advice would be to **apt-get remove --purge** mysql (and apache / php / phpmyadmin if you installed them) then use the **tasksel** utility and select the LAMP stack. This will take care of (almost) everything for you.

Thanks for your help..anyway:)

---

### Post by slavik on 2007-11-11
run top and check the memory usage ...
I know a server that I maintain has problems with MySQL when it runs out of all memory (physical and swap, haven't figured out why it runs out of memory)

---

### Post by geirha on 2007-11-11
Check /var/log/daemon.log for error messages. Try ```
grep mysql /var/log/daemon.log
```

---

### Post by Kadrus on 2007-11-11
> **geirha said:**
> Check /var/log/daemon.log for error messages. Try ```
grep mysql /var/log/daemon.log
```

When I try it I get a long message..rather a list..
and at the end it says:
```
/var/run/mysqld/mysqld.sock' exists!

```
So if I am not mistaken and I know for sure that MySql exists..but there seem to be a problem...

---

### Post by geirha on 2007-11-11
That doesn't help much. Could you post a few lines preceding and following that line too?

Does this give any output? ```
ps -ef | grep [m]ysql
```

Are you able to login with the root user using this command? ```
sudo mysql
```

---

### Post by oniiranen on 2007-11-18
I'm having a similar issue. When trying to run a cgi script I get the message:

> [Sun Nov 18 18:01:34 2007] [error] [client 127.0.0.1] Couldn't connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at /home/catoss/Desktop/catoss.com/swish-e/lib/swish-e/perl/SWISH/CatossTemplateDefault.pm line 16.

The socket address is the wrong one, but I can't seem to be able to change it. I changed the my.cnf file in /etc so that it has the proper references, but it does not seem to help because even after restart mysql still seems to look in the wrong place.

It is weird, because a .php file in a different directory connects to the mysql database just fine. When I check the system variables via phpmyadmin, phpmyadmin also shows the right socket address.

This problem was caused when I first installed mysql via xammp, and then tried to install mysql again via synaptic. I removed the synaptic installation but now things are a bit messed up.

Any ideas what the problem might be? How come some files connect to the mysql database just fine, but cgi files or command prompt don't work.

---

### Post by Kadrus on 2007-11-18
> **oniiranen said:**
> I'm having a similar issue. When trying to run a cgi script I get the message:



The socket address is the wrong one, but I can't seem to be able to change it. I changed the my.cnf file in /etc so that it has the proper references, but it does not seem to help because even after restart mysql still seems to look in the wrong place.

It is weird, because a .php file in a different directory connects to the mysql database just fine. When I check the system variables via phpmyadmin, phpmyadmin also shows the right socket address.

This problem was caused when I first installed mysql via xammp, and then tried to install mysql again via synaptic. I removed the synaptic installation but now things are a bit messed up.

Any ideas what the problem might be? How come some files connect to the mysql database just fine, but cgi files or command prompt don't work.
Obviously not me..:lolflag:...

---


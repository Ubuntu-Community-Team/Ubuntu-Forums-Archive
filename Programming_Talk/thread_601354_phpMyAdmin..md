---
title: "phpMyAdmin."
date: 2007-11-03
forum: Programming Talk
---

### Post by Kadrus on 2007-11-03
Alright I installed PHPMyAdmin through these commands

sudo apt-get install libapache2-mod-auth-mysql


sudo apt-get install php5-mysql

sudo apt-get install phpmyadmin

 and I edited the ";extension=mysql.so" part

When I open [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

With what do I login?
Any help will be appreciated :)

---

### Post by smartbei on 2007-11-03
Try root with no password - I think that is the default. A not-very-secure one, I might add.

---

### Post by 505 on 2007-11-03
try 'root' with no password. Just remember to change it.

---

### Post by Kadrus on 2007-11-03
> **505 said:**
> try 'root' with no password. Just remember to change it.

Euuh..I am getting "#1045 - Access denied for user 'root'@'localhost' (using password: NO)"
What to do?

---

### Post by smartbei on 2007-11-03
Have you tried using the password you set for the mysql root user? (Do you remember the one you set when mysql was installed?)

---

### Post by Kadrus on 2007-11-03
> **smartbei said:**
> Have you tried using the password you set for the mysql root user? (Do you remember the one you set when mysql was installed?)

Yes I wrote the password...still got access denied..never mind though..

---

### Post by aks44 on 2007-11-04
If you must reset the root password:

```
sudo /etc/init.d/mysql reset-password
```

---

### Post by Kadrus on 2007-11-04
> **aks44 said:**
> If you must reset the root password:

```
sudo /etc/init.d/mysql reset-password
```

When I do this I get 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by aks44 on 2007-11-04
> **Kadrus said:**
> When I do this I get 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

You need to start it beforehand:

```
sudo /etc/init.d/mysql start
```


Strange that it is not started automatically though.

---

### Post by Kadrus on 2007-11-04
> **aks44 said:**
> You need to start it beforehand:

```
sudo /etc/init.d/mysql start
```


Strange that it is not started automatically though.

I get this 
* Starting MySQL database server mysqld                               [fail]

---

### Post by aks44 on 2007-11-04
Now you've got two choices: either try and fix the problem, or purge/reinstall mysql-server and hope it'll work.

As far as I'm concerned, I have no clue how to find where your problem comes from... :(

---

### Post by Kadrus on 2007-11-04
> **aks44 said:**
> Now you've got two choices: either try and fix the problem, or purge/reinstall mysql-server and hope it'll work.

As far as I'm concerned, I have no clue how to find where your problem comes from... :(

No problem thanks for the help anyway :)

---

### Post by chris_lejeune on 2007-11-04
I did the LAMP install yesterday and had the same problem.  Logg'n in as root with no password didn't work for me either. So I reinstalled mysql and it worked--don't know why it didn't work to begin with though. 

Just curious, does anybody know why there a 3 root users in the user table?

---

### Post by sillv0r on 2007-11-04
> **chris_lejeune said:**
> 
Just curious, does anybody know why there a 3 root users in the user table?

Hrms, it looks as though each "root" user has a different host definition.  This might be the reasoning.  In my MySql user table:

Host                   User
127.0.0.1          root
ComputerName root
localhost            root

Not sure why though.  

I figure 127.0.0.1 and localhost are synonymous.  However, from MySql's point of view they may not be.

---


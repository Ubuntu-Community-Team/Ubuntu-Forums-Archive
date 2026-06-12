---
title: "Logging in to MySQL for the first time"
date: 2008-07-05
forum: Programming Talk
---

### Post by ceclauson on 2008-07-05
Hello!

I just installed MySQL onto my system, but don't know how to log in.

I'm trying to follow a book.  The book gave me the following command to use, but you can see the result:
```

ceclauson@ceclauson-laptop:/usr/bin$ ./mysql -h localhost -p -u root
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```
The book assumes that I know my password.  If I don't, it advises me to consult the administrator...but I think that's me.

Any help you can give would be appreciated.  Thanks in advance.

Cooper

---

### Post by ghostdog74 on 2008-07-05
dump the book and read the mysql official document instead. your question is answered [here](http://dev.mysql.com/doc/refman/5.0/en/access-denied.html)

---

### Post by tinny on 2008-07-05
> **ceclauson said:**
> Hello!

I just installed MySQL onto my system, but don't know how to log in.

I'm trying to follow a book.  The book gave me the following command to use, but you can see the result:
```

ceclauson@ceclauson-laptop:/usr/bin$ ./mysql -h localhost -p -u root
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```
The book assumes that I know my password.  If I don't, it advises me to consult the administrator...but I think that's me.

Any help you can give would be appreciated.  Thanks in advance.

Cooper

Have you run mysql_install_db ???

Three things to note.

Straight after install you need to setup the root user.

Then setup access for that user from any host (if you want).

Then enable mysql to listen for connections from remote hosts (if you want)

Do the following on the server straight after install.
```

> mysql -u root
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpwd');
mysql> SET PASSWORD FOR 'root'@'server_host_name' = PASSWORD('newpwd');


```

The root user should now be setup.

To enable root user from other hosts.

```

mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'pwd' WITH GRANT OPTION;

```

To make mysql listen for connections from other hosts (not just local) comment out "bind-address = 127.0.0.1" in /etc/mysql/my.cnf

Good luck, post back the results. :)

(this worked for me on my server)

---

### Post by unutbu on 2008-07-05
```
sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables
mysql -u root
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION; 
mysql> flush privileges
mysql> quit
sudo killall mysqld
sudo /etc/init.d/mysql start
```

---

### Post by tinny on 2008-07-05
> **unutbu said:**
> ```
sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables
mysql -u root
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION; 
mysql> flush privileges
mysql> quit
sudo killall mysqld
sudo /etc/init.d/mysql start
```


If you stop mysql how can you execute the "GRANT ALL PRIVILEGES" statement?

Or am I missing something?

OP I think this is what you want [http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html]("http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html")

---

### Post by unutbu on 2008-07-05
The command
```
sudo mysqld --skip-grant-tables
```
runs the mysql server. The --skip-grant-tables option tells the server to forget able checking permissions -- anyone can do anything. 

The method I posted is overkill. It will work if you forget your mysql root password. But for the OP's purpose, if the OP has simply never defined a password, then I think your method better because it is safer. (No one can intrude on your DB in the time it takes you to set up the password.)

---

### Post by tinny on 2008-07-06
> **unutbu said:**
> The command
```
sudo mysqld --skip-grant-tables
```
runs the mysql server. The --skip-grant-tables option tells the server to forget able checking permissions -- anyone can do anything. 

The method I posted is overkill. It will work if you forget your mysql root password. But for the OP's purpose, if the OP has simply never defined a password, then I think your method better because it is safer. (No one can intrude on your DB in the time it takes you to set up the password.)

Thanks for the clarification (I didn't know this). Really good to know if you lose your password.

---


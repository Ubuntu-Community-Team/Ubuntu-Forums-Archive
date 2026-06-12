---
title: "How to start MySQL command line in Ubuntu 11.04"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by piyushshri on 2011-10-13
I downloaded and installed MySQL with the command
```
sudo apt-get install mysql-server
```it was installed properly. Now I want to create a database and add tables to it. In Windows there used to be a command line interface where codes were written, how can I get the command line in Ubuntu?

---

### Post by sadaruwan12 on 2011-10-13
Hi hope this'll help you

[Link 1]("http://www.ubun2.com/question/357/how_connect_mysql_server_ubuntu")

[Link 2]("https://help.ubuntu.com/10.04/serverguide/C/mysql.html")

To open the terminal use Ctrl+Alt+t

---

### Post by piyushshri on 2011-10-13
Thanks for this but I am still not able to figure it out. Which IP address has to be entered here? I entered the IP address of my internet connection, it says that it could not connect.
When I used windows, there used to be an icon of mysql command line in the start menu, can't I get it here?

---

### Post by sadaruwan12 on 2011-10-13
First of I need to know R U running MySQL server locally or in a separate server?

Any way if you're running it locally then use this to get in to MySQL consol

Code:
```
mysql -u root <Give the administrator account you created when in stalling MySQL>
```

And also in Linux MySQL becomes a native service unlike in windows and also doesn't create a separate icon so you've to use the Linux terminal to access it.

It would be much easier if you user GUI front end consider installing phpMyAdmin this a web base app but grate tool and you need to have apache and php installed if you're interested in doing that here is the [link]("https://help.ubuntu.com/community/ApacheMySQLPHP") how to do that.

Note: Installing Apche, PHP and MySql doesn't slow down your PC.

---

### Post by SeijiSensei on 2011-10-13
Probably you didn't install the mysql-client package.  The server and client are packaged separately in Ubuntu.

```
sudo apt-get install mysql-client
```

Once installed, you just connect to a database like this:

```
mysql -u username -p dbname
```

The -p is optional and forces a password prompt.

After mysql-client is installed, type "man mysql" at the terminal prompt for more details.

---

### Post by piyushshri on 2011-10-13
I installed the mysql-client package. Now when I try to enter the username and database name, it shows the following error.
> ERROR 1045 (28000): Access denied for user 'piyushshri'@'localhost' (using password: YES)

---

### Post by SeijiSensei on 2011-10-13
If the account doesn't have a password, don't type -p in the command line.

If you haven't set up the accounts yet, you need to read [this](http://dev.mysql.com/doc/refman/5.5/en/adding-users.html).

Did you try connecting as user [root]("http://dev.mysql.com/doc/refman/5.5/en/default-privileges.html")?

---

### Post by piyushshri on 2011-10-13
Ok. This time I connected as root and it was successful.
Now to get the command line I have to provide a dbname, but I haven't created any databases yet. I used the command
```
create database <dbname>
```
with "hello" as the database name but when I tried to use this database to enter mysql, the following error showed up
> ERROR 1049 (42000): Unknown database 'hello'
This probaby means the database was not created. How to create a database?
and I am still not getting
mysql>
in my terminal. :(

---

### Post by piyushshri on 2011-10-13
This time I typed
```
mysql -u root -p
```
and then I entered the password. It showed up,
> Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 43
Server version: 5.1.54-1ubuntu4 (Ubuntu)

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

and the mysql command line followed.
I created a new database successfully this time.
Thanks a lot for your support. :)

---

### Post by sadaruwan12 on 2011-10-13
My friend I'm happy that you've got your problem solved.

So now please mark this thread as solved from the thread tools so we can move on.

THX

---


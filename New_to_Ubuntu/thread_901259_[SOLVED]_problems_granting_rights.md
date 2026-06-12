---
title: "[SOLVED] problems granting rights"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by ub007 on 2008-08-26
Hi,

I created a database on mysql - mail
> mysqladmin -u root -p create mail

created the user mail_admin with the passwort mail_admin_password
> GRANT SELECT, INSERT, UPDATE, DELETE ON mail.* TO 'mail_admin'@'localhost' IDENTIFIED BY 'mail_admin_password';
GRANT SELECT, INSERT, UPDATE, DELETE ON mail.* TO 'mail_admin'@'localhost.localdomain' IDENTIFIED BY 'mail_admin_password';
FLUSH PRIVILEGES;

created a table 'users' and populated it

> USE mail;
CREATE TABLE users (
email varchar(80) NOT NULL,
password varchar(20) NOT NULL,
quota INT(10) DEFAULT '10485760',
PRIMARY KEY (email)
) TYPE=MyISAM;
INSERT INTO `users` (`email`, `password`, `quota`) VALUES ('sales@example.com', ENCRYPT('secret'), 10485760);
DROP command denied to user 'mail_admin'@'localhost' for table 'forwardings' 

Now i access this though phpmyadmin
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)
But i see i have limited priveleges:
When i try to DROP table it says:
DROP command denied to user 'mail_admin'@'localhost' for table 'users' 
What do i need to do inorder to provide all priveleges.I'm the root user on this system...
Thanks in advance

Cheers
Daivd

---

### Post by cookdn on 2008-08-27
From the information supplied I guess that the 'mail' database is owned by the MySQL root user:

> mysqladmin -u root -p create mail

 and you are logging into the phpMyAdmin interface with the user 'mail_admin'; hence the message:

> DROP command denied to user 'mail_admin'@'localhost' for table 'users'

Do you know what the MySQL root user password is so that you can log into phpMyAdmin as root?

---

### Post by ub007 on 2008-08-27
> Do you know what the MySQL root user password is so that you can log into phpMyAdmin as root?

Yes,i know the password....Could you plz tell me how do  i assign the same rights to the user 'mail_admin'?

---

### Post by bodhi.zazen on 2008-08-27
```
mysql> grant all privileges on [databasename].* to [dbusername]@localhost identified by '[dbpassword]';
```[FONT=arial, verdana, helvetica]

[http://www.pantz.org/software/mysql/mysqlcommands.html](http://www.pantz.org/software/mysql/mysqlcommands.html)
[/FONT]

---

### Post by ub007 on 2008-08-28
Thanks mate

---


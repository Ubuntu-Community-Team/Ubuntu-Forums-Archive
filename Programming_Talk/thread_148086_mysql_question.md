---
title: "mysql question"
date: 2006-03-21
forum: Programming Talk
---

### Post by robtotheb on 2006-03-21
Im following a tutorial on Ruby on Rails and can't work out what im doing wrong with regards to this....

```

rob@ubuntu:~/work/depot$ mysql depot_development <db/create.sql
ERROR 1045 (28000): Access denied for user 'rob'@'localhost' (using password: NO)

```

No idea what that means. :confused:

---

### Post by gnu2tux on 2006-03-21
It means you haven't provided a password to log into mysql with. Naturally if you use a password for the user rob, this will fail.

try this instead:

rob@ubuntu:~/work/depot$ mysql depot_development --password="mypass" <db/create.sql

-p also works interactively, but if you are doing redirection like this I think --password is better.

Regards,

Ali

---

### Post by robtotheb on 2006-03-21
Thanks gnu2tux but I still get the same error.

---

### Post by gnu2tux on 2006-03-21
What - even the part about '(using password: NO)'? !!?

have you actually set up the user 'rob' in your mysql database?

Which user should you be loading the 'db/create.sql' script as, eg, should it be loaded as rob, or what about root? (add -u root to command line)

Check your database settings and come back.

Regards,

Al.

---

### Post by robtotheb on 2006-03-22
OK im totally confused now.  ](*,) 

The book im following (Agile Web Developement with Rails) asked me to do the following:

```
work> rails depot
```

no problems

```

depot> mysql -u root -p
Enter password: *******
Welcome to the MySQL monitor.  Commands end with ; or \g.
mysql> create database depot_development;
mysql> create database depot_test;
mysql> create database depot_production;
mysql> grant all on depot_development.* to 'rob'@'localhost';
mysql> grant all on depot_test.* to 'rob'@'localhost';
mysql> grant all on depot_production.* to 'prod'@'localhost' identified by wibble';
mysql> exit

```

no prob

Next I create a sql file (create.sql):

```
drop table if exists products;
create table products (
 id		int           not null auto_increment,
 title       	varchar(100)  not null,
 description	text          not null,
 image_url	varchar(200)  not null,
 price		decimal(10,2) not null,
 primary key 	(id)
);
```

When I try to create the table in my development database:

```
rob@ubuntu:~/work/depot$ mysql depot_development <db/create.sql
ERROR 1045 (28000): Access denied for user 'rob'@'localhost' (using password: NO)
```

I'm really confused with how to set up mysql.

---

### Post by zootreeves on 2006-03-22
Can you connect as the root user?

---

### Post by robtotheb on 2006-03-22
depot> mysql -u root -p
Enter password: *******
Welcome to the MySQL monitor.  Commands end with ; or \g.

Yes.  I have set a password for it

---

### Post by mhafren on 2006-03-23
```
 *mysql> grant all on depot_development.* to 'rob'@'localhost'; 
```*

Change it to:
```

**mysql> grant all on depot_development.* to 'rob'@'localhost' IDENTIFIED BY 'password';**

```

When I try to create the table in my development database:

```
[I]rob@ubuntu:~/work/depot$ mysql depot_development <db/create.sql
ERROR 1045 (28000): Access denied for user 'rob'@'localhost' (using password: NO)[/I]
```

Here you should provide a password, try:
```

**mysql depot_development -urob -p <db/create.sql**

```
Provide the password for rob when prompted.
Hope this helps..

---

### Post by robtotheb on 2006-03-23
It did thanks.

note: any one trying to get rails to run with mysql these links are very helpful
[http://www.ubuntuforums.org/showthread.php?t=136712]("http://www.ubuntuforums.org/showthread.php?t=136712")
[http://paulgoscicki.com/archives/2005/09/ruby-on-rails-on-ubuntu/]("http://paulgoscicki.com/archives/2005/09/ruby-on-rails-on-ubuntu/")

---


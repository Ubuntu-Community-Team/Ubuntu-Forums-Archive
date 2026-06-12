---
title: "create new database in MySQL without using root"
date: 2009-06-23
forum: Programming Talk
---

### Post by Krijk on 2009-06-23
I'm trying to figure out if it is possible to create a database in MySQL without having to use the MySQL root-user.

I use a plain text configuration file with the user and password for the creation script (Python) of database and tables. Obviously I don't want to put the root password in it. 

I figure that I can create a single database. Give the rights and create tables such as:

database.database1_table1
database.database1_table2
database.database2_table1
database.database2_table2

But since I have a lot of tables in a single database this will probably add a lot of complexity.


Does anybody have a workaround for this?

---

### Post by Wim Sturkenboom on 2009-06-23
Do you have the option to create a mysql user before you run the script? If so, you can give that user permissions to create databases and tables and use that user to in your script.

---

### Post by Krijk on 2009-06-23
> **Wim Sturkenboom said:**
> Do you have the option to create a mysql user before you run the script? If so, you can give that user permissions to create databases and tables and use that user to in your script.


I have given the user CREATE rights on the mysql database. I'm not sure how to give the user permissions to create a database. Creating tables isn't an issue. I give the user all but GRANT rights on the database I manually created with root.

---

### Post by Can+~ on 2009-06-23
Create a Database with a new user (could be named as your ubuntu account) with permissions to do everything you need on that Database. Then create a .sql with something like:

[PHP]USE mydatabase;

CREATE TABLE tablename
(
   etc etc..
) ENGINE = InnoDB;

INSERT INTO...[/PHP]

(Notice the "USE", it allows to select an specific database, other Mysql-only commands include: SHOW TABLES, SHOW DATABASES)

Then run your script with

mysql -u username -p < myfile.sql

Also, you can execute the batch SQL file including the name of the database so you don't have to use "USE dbname", making it "more portable" (but it's just one line of difference really)

> **Krijk said:**
> I have given the user CREATE rights on the mysql database. I'm not sure how to give the user permissions to create a database. Creating tables isn't an issue. I give the user all but GRANT rights on the database I manually created with root.

Why would you? The idea of "Databases" is to enclose a set of tables to tackle a problem, in what case you need to frequently create new databases?

---

### Post by Krijk on 2009-06-23
> **Can+~ said:**
> Create a Database with a new user (could be named as your ubuntu account) with permissions to do everything you need on that Database. 


This is the issue I want to script. In the script I check if the database exists, if not I want to create it. 

[PHP]sql = "CREATE SCHEMA IF NOT EXISTS `%s` DEFAULT CHARACTER SET latin1 COLLATE latin1_swedish_ci ;" % (databasename)[/PHP]

When I run it to create a new database it gives the following errors:

_mysql_exceptions.OperationalError: (1044, "Access denied for user 'test'@'%' to database 'testmynewdb'")

---

### Post by Can+~ on 2009-06-23
Well, it's python after all, so you could do:

[PHP]#blah blah...

print "Creating Databases, this requires root authentication"
rootpassword = raw_input("Root password:")

#yadah yadah..

sql = "CREATE SCHEMA IF NOT EXISTS `%s` DEFAULT CHARACTER SET latin1 COLLATE latin1_swedish_ci ;" % (databasename)

# *use root password here*[/PHP]

Or... having the root password accepted through sys.argv and run your script

myscript -p rootpassword

There's also a module for handling commandline arguments, [getopt]("http://docs.python.org/library/getopt.html").

(Example from the python doc)
[PHP]
>>> import getopt
>>> args = '-a -b -cfoo -d bar a1 a2'.split()
>>> args
['-a', '-b', '-cfoo', '-d', 'bar', 'a1', 'a2']
>>> optlist, args = getopt.getopt(args, 'abc:d:')
>>> optlist
[('-a', ''), ('-b', ''), ('-c', 'foo'), ('-d', 'bar')]
>>> args
['a1', 'a2']
[/PHP]

---

### Post by Krijk on 2009-06-24
> **Can+~ said:**
> Well, it's python after all, so you could do:

[PHP]#blah blah...

print "Creating Databases, this requires root authentication"
rootpassword = raw_input("Root password:")


The problem is that it is a scheduled job that runs every hour or so, so no userinput can be given.
Maybe I should switch the database to PostgreSQL because it can allow users to create databases.

---

### Post by Wim Sturkenboom on 2009-06-25
You must have done something wrong that you get the 'access denied' error.
```

[COLOR="SeaGreen"]// THIS CODE WORKS[/COLOR]
wim@btd-techweb01:~$ mysql -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 280692 to server version: 4.0.23a

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> grant create on *.* to 'pietje'@'%' identified by 'pietje';
Query OK, 0 rows affected (0.00 sec)

mysql> show grants for 'pietje'@'%';
+-------------------------------------------------------------------------------+
| Grants for pietje@%                                                           |
+-------------------------------------------------------------------------------+
| GRANT CREATE ON *.* TO 'pietje'@'%' IDENTIFIED BY PASSWORD '2761dc0b290a8d88' |
+-------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> exit
Bye
wim@btd-techweb01:~$ mysql -u pietje -ppietje
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 280693 to server version: 4.0.23a

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database pietje;
Query OK, 1 row affected (0.00 sec)

mysql> exit
Bye
wim@btd-techweb01:~$

```

One of the reasons for the error might have been that you forgot to flush the privileges (although I also seem to have forgotten it). Another reason can be that the user exists for both localhost (without create privilege) and wildcard (with create privilege) as shown below. (I ran into that one initially).
```

[COLOR="Red"]THIS CODE DOES NOT WORK (access denied)[/COLOR]
wim@btd-techweb01:~$ mysql -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 280694 to server version: 4.0.23a

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> grant create on *.* to 'pipo'@'localhost' identified by 'pipo';
Query OK, 0 rows affected (0.00 sec)

mysql> show grants for 'pipo'@'localhost';
+-------------------------------------------------------------------------------------+
| Grants for pipo@localhost                                                           |
+-------------------------------------------------------------------------------------+
| GRANT CREATE ON *.* TO 'pipo'@'localhost' IDENTIFIED BY PASSWORD '230b4e9e4f23bb86' |
+-------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> revoke all on *.* from pipo@localhost;
Query OK, 0 rows affected (0.01 sec)

mysql> show grants for pipo@localhost;
+------------------------------------------------------------------------------------+
| Grants for pipo@localhost                                                          |
+------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'pipo'@'localhost' IDENTIFIED BY PASSWORD '230b4e9e4f23bb86' |
+------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> grant create on *.* to 'pipo'@'%' identified by 'pipo';
Query OK, 0 rows affected (0.00 sec)

mysql> show grants for 'pipo'@'%';
+-----------------------------------------------------------------------------+
| Grants for pipo@%                                                           |
+-----------------------------------------------------------------------------+
| GRANT CREATE ON *.* TO 'pipo'@'%' IDENTIFIED BY PASSWORD '230b4e9e4f23bb86' |
+-----------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.01 sec)

mysql> exit
Bye
wim@btd-techweb01:~$ mysql -u pipo -ppipo
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 280703 to server version: 4.0.23a

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database pipo;
ERROR 1044: Access denied for user: 'pipo@localhost' to database 'pipo'
mysql>

```
I think that in this situation pipo@localhost is more specific than pipo@%and therefore has preference.

Hope this helps (tested on version 4.0.23a).

---

### Post by Krijk on 2009-06-25
> **Wim Sturkenboom said:**
> You must have done something wrong that you get the 'access denied' error.

Hope this helps (tested on version 4.0.23a).


You're right Wim. I didn't give the required rights. I only gave limited create-rights, not on everything. When I used:

```
 grant create on *.* to 'mamaloe'@'%' identified by 'woonwagen';
```

The script worked fine.

---

### Post by Wim Sturkenboom on 2009-06-25
OK, do you want me to change pipo's password to 'de clown' :D

---

### Post by Krijk on 2009-06-25
> **Wim Sturkenboom said:**
> OK, do you want me to change pipo's password to 'de clown' :D

That's my very secret password :biggrin:

---


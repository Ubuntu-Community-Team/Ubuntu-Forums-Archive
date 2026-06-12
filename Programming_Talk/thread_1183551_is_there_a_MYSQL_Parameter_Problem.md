---
title: "is there a MYSQL Parameter Problem?"
date: 2009-06-10
forum: Programming Talk
---

### Post by daspedal on 2009-06-10
heyo,

i'd just installed apache2,php5+mysql by dpkg and when i tried to import a .sql file following stuff happened:

> 
manfred@manfred-ibex:~$ mysql -u test -p passwort -h localhost -D test < input_file.sql
Enter password: 
ERROR 1044 (42000): Access denied for user 'test'@'localhost' to database 'passwort'
manfred@manfred-ibex:~$ mysql -u test -p passwort -h localhost -D test < input_file.sql
Enter password: 
ERROR 1045 (28000): Access denied for user 'test'@'localhost' (using password: YES)
manfred@manfred-ibex:~$ mysql -u test -D test < input_file.sql
ERROR 1045 (28000): Access denied for user 'test'@'localhost' (using password: NO)
manfred@manfred-ibex:~$ mysql -u test -p passwort -D test < input_file.sql
Enter password: 
ERROR 1044 (42000): Access denied for user 'test'@'localhost' to database 'passwort'
manfred@manfred-ibex:~$ mysql -u test -p passwort -D test < "input_file.sql"
Enter password: 
ERROR 1045 (28000): Access denied for user 'test'@'localhost' (using password: YES)
manfred@manfred-ibex:~$ mysql -u test -D test < "input_file.sql"
ERROR 1045 (28000): Access denied for user 'test'@'localhost' (using password: NO)
manfred@manfred-ibex:~$ mysql -u test -p passwort
Enter password: 
ERROR 1044 (42000): Access denied for user 'test'@'localhost' to database 'passwort'
manfred@manfred-ibex:~$ mysql -u test -p test
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 35
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> Aborted


when asking help it definitly says that -p is for pass and -D for database
> 
manfred@manfred-ibex:~$ mysql --help
  ...
  -D, --database=name Database to use.
  ...
  -p, --password[=name] 
                      Password to use when connecting to server. If password is
                      not given it's asked from the tty. WARNING: This is
                      insecure as the password is visible for anyone through
                      /proc for a short time.
  ...


...so i tried switching the parameters and everything works fine...

> 
manfred@manfred-ibex:~$ mysql -u test -p test < input_file.sql
Enter password: 
manfred@manfred-ibex:~$ 


> 
manfred@manfred-ibex:~$ mysql -u test -p passwort
Enter password: 
ERROR 1044 (42000): Access denied for user 'test'@'localhost' to database 'passwort'
manfred@manfred-ibex:~$ 


someone else got that "problem"??

---

### Post by Arndt on 2009-06-10
> **daspedal said:**
> heyo,

i'd just installed apache2,php5+mysql by dpkg and when i tried to import a .sql file following stuff happened:



when asking help it definitly says that -p is for pass and -D for database


...so i tried switching the parameters and everything works fine...





someone else got that "problem"??

Apparently -p alone means that it should ask for password, and -ppasswort that you give that password on the command line. In -p passwort, "passwort" becomes the next option, and is presumably ignored in your second case, since it comes last.

---

### Post by The Cog on 2009-06-10
The way I read that help file, if you want to supply a password on the command line then you have to use --password=passwort. I think the short form "-p" can only be used to tell it to prompt for a password.

---


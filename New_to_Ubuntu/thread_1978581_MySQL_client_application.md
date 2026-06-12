---
title: "MySQL client application?"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-12
Hey guys, I am looking for a user friendly MySQL Admin tool that has an simple/clean UI. There used to be one in the Ubuntu Software Centre when I was using 11.10 (wish I remembered the name) but nothing is returned when I search now with a clean install of 12.04....Is there something like Navicat or even an official MySQL client version for linux that I can install to administer my remote databses with an easy to use interface?  :confused:

---

### Post by Gone fishing on 2012-05-12
Something like phpMyAdmin [http://www.phpmyadmin.net](http://www.phpmyadmin.net)

You could have a look at [https://help.ubuntu.com/12.04/serverguide/phpmyadmin.html](https://help.ubuntu.com/12.04/serverguide/phpmyadmin.html) and you can install with apt-get

---

### Post by d4m1r on 2012-05-12
I know of PMA but I am looking for a client application that I had to install...Not a web one like PMA which would require me to setup a web server locally and other things.

What is everyone else using to connect to their MySQL servers? :confused:

---

### Post by steeldriver on 2012-05-12
I've used SQuirrel to connect to a MSSQL box, it supports pretty much any backend though  - I only really tried it to see if I could (didn't use it in anger) but it appears to be quite full featured  - SQL syntax highlighting etc.

---

### Post by SeijiSensei on 2012-05-12
I prefer PostgreSQL, but for both it and MySQL I just use the native command-line clients (psql and mysql) and enter the SQL commands I need.  PostgreSQL has a few nice command-line utilities like "createuser" and "createdb" for those specific admin tasks.  One reason I avoid MySQL is its annoying techniques for creating users and databases.

---

### Post by Gone fishing on 2012-05-12
Have a look at [http://www.mittalpatel.co.in/access_mysql_database_hosted_remote_server_using_phpmyadmin](http://www.mittalpatel.co.in/access_mysql_database_hosted_remote_server_using_phpmyadmin) phpmyadmin can administer a remote server

---

### Post by Hilgo on 2012-05-12
What about [MySQL Workbench]("http://www.mysql.com/products/workbench/")?

---

### Post by d4m1r on 2012-05-12
Thanks for all the tips guys but I finally found a comparably replacement in the Ubuntu Software Centre. It's called Emma, and I think it is an official release for managing a MySQL DB through a UI in linux.

The UI is OK and better than command line, but not as good as whatever I was using under 11.10...Anyway, it does the trick so search for it if you need something similar :)

---

### Post by krippa on 2012-05-15
Maybe it was mysql-admin that you were using? This was part of the mysql GUI tools that has reached end of life. There is however a replacement available in the universe repos in precise: mysql-workbench which seems pretty complete.

---

### Post by tom anderson on 2013-04-01
You can use Valentina Studio [http://www.valentina-db.com/en/valentina-studio-overview](http://www.valentina-db.com/en/valentina-studio-overview), 14 Feb 2013 in the 5.0 version added support of mySQL/mariaDB, as well as, SQLite, PostgreSQL. It is FREE. Works on Mac, Win and Linux. Includes not only db management but powerfull reports that work again on 3 OS. I am very pleased with this program

 [IMG]http://www.valentina-db.com/images/products/valentina5/studio/valentina5interface_1_765x506.png[/IMG]

---

### Post by ronald577 on 2013-04-01
Thanks for providing the snapshot.

---


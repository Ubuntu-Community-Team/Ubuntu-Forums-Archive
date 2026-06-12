---
title: "[SOLVED] How to install MySQL?"
date: 2008-04-11
forum: Programming Talk
---

### Post by GoCool on 2008-04-11
I have a working knowledge on SQL but never configured a database environment. The maximum experience I have is to install MS Access in Windows environment.

1. How much of a task is to install MySQL in my ubuntu?
(I saw the repository and it has lots of choices on MySQL, hope if I pick one, it will automatically check all the other dependencies. But still would appreciate a dummy's instruction for me)

2.Can I have a simple front end where I can practise my SQL queries?
(Hopefully I'll have a database and a sample table, else no big deal I can create one. But how do we get into it. A dummy's instruction would be appreciated. For Oracle I can use Toad, for MS SQL I can use SQL Navigator etc, similarly any easy on eye front end for MySQL would be great)

3. Any good tutorial on MySQL
(Not fancy one, but something which I can enjoy reading and doing without much hassle)

---

### Post by Can+~ on 2008-04-11
1.[PHP]sudo apt-get install mysql-admin mysql-server[/PHP]
(This are dummy packages, they download the latest version).

2.mysql-admin comes with a nice GUI and a query browser, so you can start quering.

3.[w3schools](http://www.w3schools.com/sql/sql_intro.asp)

---

### Post by GoCool on 2008-04-11
Thank you friend, I got it.

But when I open the navigator its asking for 
1.Host
2.User
3.Password
4. Database
5. Port
6. Socket
7. Timeout

I remember it did ask me for the password while installing, which is all I remember, but I did not note the rest of the information. 

So is there any configuration file which I can check and fill in the details? 

Thank you for the tutorials, but I need a tutorial on MySQL not SQL. Like administrative tasks etc. Thank you again.

If yes, then  where can I find this information?

---

### Post by bobbocanfly on 2008-04-11
> **GoCool said:**
> Thank you friend, I got it.

But when I open the navigator its asking for 
1.Host
2.User
3.Password
4. Database
5. Port
6. Socket
7. Timeout

I remember it did ask me for the password while installing, which is all I remember, but I did not note the rest of the information. 

So is there any configuration file which I can check and fill in the details? 

Thank you for the tutorials, but I need a tutorial on MySQL not SQL. Like administrative tasks etc. Thank you again.

If yes, then  where can I find this information?

1.Host - probably 'localhost' if you installed it on the machine you are trying to access it from
2.User - root probably
3.Password - self explanatory
4. Database - Not sure
5. Port _probably 3306
6. Socket - Not sure again
7. Timeout - Not sure

---

### Post by LaRoza on 2008-04-11
> **GoCool said:**
> 
Thank you for the tutorials, but I need a tutorial on MySQL not SQL. Like administrative tasks etc. Thank you again.

If yes, then  where can I find this information?

[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

---

### Post by LaRoza on 2008-04-11
> **GoCool said:**
> 

2.Can I have a simple front end where I can practise my SQL queries?
(Hopefully I'll have a database and a sample table, else no big deal I can create one. But how do we get into it. A dummy's instruction would be appreciated. For Oracle I can use Toad, for MS SQL I can use SQL Navigator etc, similarly any easy on eye front end for MySQL would be great)

3. Any good tutorial on MySQL
(Not fancy one, but something which I can enjoy reading and doing without much hassle)

After it is installed, type:

```

mysql -u root

```

You can execute SQL from here.

---

### Post by Can+~ on 2008-04-11
Mysql-admin:

-Schema privilges: Under User administration, you can create new users to access your databases, you grant them access to the "catalog" they need and what functions they can use.

-Catalogs: Create a new starting catalog, add a table inside.

Once you have both a table and a user that can access it (by default, root can access everything, but it's a good practice to have a lesser power account that access the data).

Later, once everything is set, you can open the Mysql query browser and add queries and see what happens graphically.

Or you could do like LaRoza and login through the shell.

---

### Post by LaRoza on 2008-04-11
> **Can+~ said:**
> 
Or you could do like LaRoza and login through the shell.

That is how I learned (and still use it mostly).

To make a testing database (if it doesn't come with one) you can make it with:

```

mysql> create database testing;
mysql> use testing;

```

From there you have an empty database and can proceed to make tables.

---

### Post by GoCool on 2008-04-11
Thank you all for the help. True to the spirit of Ubuntu, extremely impressed.

---


---
title: "can insert values in database, but not select from it"
date: 2012-11-06
forum: Programming Talk
---

### Post by sid0972 on 2012-11-06
as the title says, can insert values in database, but while selecting from it, en error comes

```
Unable to select mydbname: Access denied for user ''@'localhost' to database 'testdb'

```

inserting the values through php, and retrieving from it too, database is mysql

what could be the issue?
it maybe the privileges but i am not very proficient in it

---

### Post by SeijiSensei on 2012-11-06
You haven't specified the name of the MySQL user that owns the database.  Where you do this depends entirely on the application.  However if you can write into the database, then the script that handles that task must be connecting with the correct username. See if you can figure out where it is getting the name from.

---

### Post by sid0972 on 2012-11-06
i dont know how is it doing that 
what i wrote was

```

$conn=new mysqli('localhost','root','password','db_name');

```

everywhere its the same, at least in the case when i write into database

---

### Post by SeijiSensei on 2012-11-08
Well since the error reads

```
Access denied for user ''@'localhost'
```

and not 'root'@'localhost', the application is not using the name you specified.

---

### Post by sid0972 on 2012-11-11
any idea how that could be solved??

---

### Post by kevinharper on 2012-11-11
Maybe the error is where these variables are declared and/or assigned a value.

---

### Post by sid0972 on 2012-11-11
> **kevinharper said:**
> Maybe the error is where these variables are declared and/or assigned a value.

i dont know, when i execute the same query in mysql through terminal, it gives me the proper output, and i searched like 100 forums only to find out nothing

---

### Post by kevinharper on 2012-11-11
I think a bit more code would help in trying to identify the issue.

It's possible that the problem isn't actually on the line you've already posted.

Here's a good example of how to connect
[http://php.net/manual/en/mysqli.quickstart.connections.php](http://php.net/manual/en/mysqli.quickstart.connections.php)

---

### Post by spjackson on 2012-11-12
> **sid0972 said:**
> as the title says, can insert values in database, but while selecting from it, en error comes

```
Unable to select mydbname: Access denied for user ''@'localhost' to database 'testdb'

```

inserting the values through php, and retrieving from it too, database is mysql

what could be the issue?
it maybe the privileges but i am not very proficient in it

> **sid0972 said:**
> i dont know how is it doing that 
what i wrote was

```

$conn=new mysqli('localhost','root','password','db_name');

```

everywhere its the same, at least in the case when i write into database
If you were using variables as parameters to mysqli, I would suggest printing these out immediately before trying to connect. Since you are using string literals, I can't see how you get that error message showing an empty username.

What statement gives rise to the error? Is it the above connect, or is it a subsequent select?

---

### Post by kevinharper on 2012-11-12
Yep. A little more code would be very helpful.

---

### Post by sid0972 on 2012-11-13
ok i'll post as soon as i get time
its festive season here in india

---

### Post by kevinharper on 2012-11-13
Happy Diwali. Celebrate safely.

---

### Post by sid0972 on 2012-11-16
happy belated diwali to you too

---

### Post by sid0972 on 2012-11-29
hey
bumping this thread
i solved the previous problem of mine, used another code, and got the output
but i have another issue now

when i insert some values for a user in a table, the query creates a new user itself!!

my users.sql file is this

```
create table users(user_id mediumint(8) unsigned not null primary key auto_increment,
 username varchar(32) not null,
 user_pass varchar(40) not null,
 user_email varchar(100) not null,
 user_bday varchar(10),
 user_lastvisit int(11) unsigned, 
 user_login_attemps tinyint(4),
 user_posts mediumint(8) unsigned not null,
 user_allow_viewonline tinyint(1) unsigned,
 user_avatar varchar(40),
 user_location varchar(20),
 user_newpass varchar(40),
 user_occupation varchar(40));
```and this code inserts values in the table
```

<?php
session_start();
require_once('fns.php');


$aname=$_POST['aname'];

$occupation=$_POST['occupation'];
$location=$_POST['location'];

$conn=db_connect();
 $result=$conn->query("insert into users (user_aname,user_location,user_occupation) values ('".$aname."','".$location."','".$occupation."')");
 
 if(!$result)
 {
     echo "couldnt do it, sorry!!";
 }

    if ($result->num_rows>0) {
    throw new Exception('Duplicate Details.');
  }
else{
echo "Details saved";}


```the output of select * from users in mysql cli is this 

```
mysql> select * from users;
+---------+----------+------------------------------------------+---------------------+-----------+----------------+--------------------+------------+-----------------------+-------------+---------------+--------------+-----------------+------------+
| user_id | username | user_pass                                | user_email          | user_bday | user_lastvisit | user_login_attemps | user_posts | user_allow_viewonline | user_avatar | user_location | user_newpass | user_occupation | user_aname |
+---------+----------+------------------------------------------+---------------------+-----------+----------------+--------------------+------------+-----------------------+-------------+---------------+--------------+-----------------+------------+
|       5 | sid      | b1b3773a05c0ed0176787a4f1574ff0075f7521e | sid0972@yahoo.co.in | NULL      |           NULL |               NULL |          0 |                  NULL | NULL        | NULL          | NULL         | NULL            | NULL       |
|       6 |          |                                          |                     | NULL      |           NULL |               NULL |          0 |                  NULL | NULL        | a             | NULL         | a               | a          |
+---------+----------+------------------------------------------+---------------------+-----------+----------------+--------------------+------------+-----------------------+-------------+---------------+--------------+-----------------+------------+
2 rows in set (0.00 sec)

```as you can see, i inserted the last two values and 4th last value in a query from php, and instead of inserting it in user_id=5, it created a whole new user (user_id=6, )

is this cause of auto_increment i used while creating the table??

---

### Post by SeijiSensei on 2012-11-29
Personally I rarely use autoincrement fields to create primary keys.  My preferred choice is the unix datestamp (what you get with the command "date +%s" in the terminal).  That kills two birds with one stone.  Each record has a unique ID, as long as at least a second passes between entries, and the ID tells you when the record was created.

In PHP, the time() function returns the datestamp.

---

### Post by sid0972 on 2012-11-30
thank you for the reply

your method is good but frankly, its over my head, so i'll revert to it as a last stand.

EDIT: i am trying another approach now
while inserting values in the database, i am trying to include the where clause, "insert this while username=$name";

but i cant get the current username
how do i get it??
i am trying this code

```
$name=$_SESSION['valid_user'];
```

but this is not working

---


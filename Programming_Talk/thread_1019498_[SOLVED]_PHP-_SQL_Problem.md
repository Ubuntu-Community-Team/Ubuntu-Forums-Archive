---
title: "[SOLVED] PHP- SQL Problem"
date: 2008-12-23
forum: Programming Talk
---

### Post by s.fox on 2008-12-23
Hi,

I feel like I am going insane.  What on earth is wrong with the script I posted below?  The script dies because of the SQL I am trying to run.   The database login credentials are correct,  as is the SQL itself.

[php]
$email = "example@example.com";

$host="localhost"; 

$username="username"; 

$password="pass"; 

$db_name="databaseName";

$connection = mysql_connect("$host", "$username", "$password")or die("cannot connect");
$query="SELECT userEmail,userID,userPassword,userUserName FROM user WHERE user.userEmail = 
'$email'";

$st=mysql_query($query, $connection) or die("died because of $query");

$recs=mysql_num_rows($st) or die("died because of recs");

$row=mysql_fetch_object($st) or die ("died because of row");[/php]

Really stuck and very confused.  Can anyone spot what the problem is?

Many thanks,  Ash R

---

### Post by mike_g on 2008-12-23
You will need to select the databse you want to work with after connecting. See [mysql_select_db](http://uk2.php.net/mysql_select_db)
Used like:
```
mysql_select_db($db_name);
```
Also, you can gett better debug output by using mysql_error() when you query. IE:
```
$st=mysql_query($query, $connection) or die(mysql_error());
```

---

### Post by s.fox on 2008-12-23
doh!  I should have spotted that one.   Now the script works how I want :)

Thanks for the tip about the mysql_error.  I usually don't use it but I think i may start to with more regularity.  Incidentally I finally managed to get full database access so I was able to create all my tables without to much hassle. 

Cheers Mike for all the help you have given me over the last few days.

---

### Post by mike_g on 2008-12-23
No worries, have fun with it :)

---


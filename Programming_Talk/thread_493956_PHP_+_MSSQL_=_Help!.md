---
title: "PHP + MSSQL = Help!"
date: 2007-07-06
forum: Programming Talk
---

### Post by dhtseany on 2007-07-06
Hi guy, I'm here is what I'm trying to do:

We have a MS-SQL server where my telemarketing company stores their dialing leads (Lname, Fname, PhoneNum, etc.) for our dialers. What we're looking to do is create a simple, web based page where our agents can search our tables for any records they need to obtain their customer's info. I've successfully setup the server running LAME. I've tested everything and all is running correctly. What I can't figure out it where to start on the actual development side. I've found a few examples online but all of them return PHP errors. Does anyone have a suggestion on where I should go from here? Keep in mind the only thing this server will do is "view" the records. We do not intend to allow our agents modify anything, so it's all strictly read only. 

So I'm lost, any ideas?

---

### Post by LaRoza on 2007-07-06
How much experience with MySQL and PHP do you have? It may be easier to get a working example of PHP+MySQL.

[http://www.tizag.com/](http://www.tizag.com/) has tutorials on the subject.

I suggest using the mysqli functions, they are better.

(What errors are you getting, post them)

---

### Post by LaRoza on 2007-07-06
How to connect:

```

<?php
 $connection=mysqli_connect('localhost','name','password','database') or die(mysqli_error());
 ?>

```
I suggest you keep the connection in an include file so you can reuse it, and update it easily.

How to get results:
```

   require_once('includes/connection.inc'); 
   $query = "SELECT UserName FROM users ORDER BY AgentID";
   $results = mysqli_query($connection,$query); 

```
You can put the SQL string in the function "mysqli_query" also, but it is better to construct the string then store it in a variable.


How to create a table with results:
```

while($result=mysqli_fetch_array($results))
{
   $UserName= $result['UserName'];
   echo<<< EOF
   <tr>
   <td>$UserName</td>
   </tr>
   EOF;
}

   echo "</table>";
   mysqli_close($connection);


```

This is not want you are looking for, but it demonstrates how the query works.

(Thank Opera for it "Notes".)

---

### Post by dhtseany on 2007-07-06
Hey guys, thanks for hitting me back. I have a working knowledge of SQL (mainly running queries) however I'm a bit rusty on my PHP. 

Please note that I'm using MSSQL, not MySql. Will the commands be the same between My and MS? Ex:

```
<?php
 $connection=**mysqli**_connect('localhost','name','password','database') or die(mysqli_error());
 ?>
```


Also, I tried running just the connecting script and this is what I got:
```
Fatal error: Call to undefined function mysqli_connect() in /home/sean/www/php.php on line 2
```

---

### Post by dhtseany on 2007-07-06
Rebumping

---

### Post by maddog39 on 2007-07-06
Everyone here is trying to get you to use MySQL, but you said your company is running Microsoft SQL (MSSQL) and therefore MySQL wont work, and I doubt your company will be willing to switch.

[http://us2.php.net/manual/en/ref.mssql.php](http://us2.php.net/manual/en/ref.mssql.php)

There is the MSSQL reference on the PHP website.

[Edit]
The mysqli_* functions only work on PHP5 as well, by the way.

---

### Post by runningwithscissors on 2007-07-07
You need unixODBC and freetds installed and configured to work with MSSQL databases from a unix php installation.

---

### Post by dhtseany on 2007-07-09
> **runningwithscissors said:**
> You need unixODBC and freetds installed and configured to work with MSSQL databases from a unix php installation.

Is there a page that shows how to do this anywhere?

---

### Post by LaRoza on 2007-07-09
[http://www.unixodbc.org/doc/FreeTDS.html](http://www.unixodbc.org/doc/FreeTDS.html)

---


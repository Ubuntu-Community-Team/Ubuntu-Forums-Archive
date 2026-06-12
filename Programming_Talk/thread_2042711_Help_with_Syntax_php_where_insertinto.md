---
title: "Help with Syntax php where insertinto"
date: 2012-08-15
forum: Programming Talk
---

### Post by 0akash0 on 2012-08-15
Dear Experts,

I am getting a syntax error. I have very little knowledge of PHP, I have been trying to cobble up a small form to insert a text value into a specific field in a specific row in a table in a database.

This is the form code:
```

<HTML>
<form action="script.php" method="post"/>
<p>Input Name: <input type="text" name="name"</p> 
//name already exists in the table
<p>Input Code: <input type="text" name="code"</p> 
//need to add this value to a field called code only for that name
<input type="submit" value="Submit" />
</form>
</HTML>

```

This is the PHP Script:
```

<?php
$name = $_POST['name'];
$jobs = $_POST['code'];
echo "Refer to list of Profession ID's and enter details accordingly";
mysql_connect ("localhost", "root", "") or die ('Error: ' . mysql_error());
mysql_select_db ("office_db");

$query="INSERT INTO personal WHERE name='".$name."' (code) VALUES ('".$code."');

mysql_query($query) or die ('Error updating databse');

echo "Database Updated";
?>

```


I understand this is a very basic syntax error, and I am not knowledgeable about it at all. Kindly help me with this and I shall be very grateful. 
Thank you.

PS: I know this is an Ubuntu Forum and not a PHP forum, but I didn't know where else to turn :( Sorry if I have wasted your time.

---

### Post by Elfy on 2012-08-16
*Thread moved to **Programming Talk**.*

---

### Post by DarkAmbient on 2012-08-16
Just a pointer, add this to your index.php.

```
error_reporting(E_ALL);
ini_set('display_errors', '1');
``` 

Then php will tell you of all the errors, just don't use it on live sites.

---

### Post by spjackson on 2012-08-16
One issue is that you have
```

$jobs = $_POST['code'];

```but then in the query you use $code which is not set. If you want to use $code in your query, then set it to the right value. Otherwise use $jobs. Note that $code could be set if you are using a very old version of PHP or if you are using the register globals option. This is a bad idea and has been removed in the latest php. 

Secondly, judging from your WHERE clause, it looks like you are wanting to update a row that already exists. You do this via an UPDATE statement, thus.
```

$query="UPDATE personal SET code = '$jobs' WHERE name='$name'";

```INSERT is for inserting new rows. It does not accept a WHERE clause, [see here]("http://dev.mysql.com/doc/refman/5.5/en/insert.html").

Thirdly, it is a bad (dangerous) idea to take user input and insert it directly into a database query without validation. This is known as [SQL Injection]("http://php.net/manual/en/security.database.sql-injection.php").

Finally, consider using [PDO]("http://www.php.net/manual/en/book.pdo.php") instead of the mysql_* functions.

---


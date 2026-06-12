---
title: "Trying to get an editing option with PHP and MySQL"
date: 2009-12-02
forum: Programming Talk
---

### Post by dmillerw on 2009-12-02
Basically, I've got a database full of data, and would like people to be able to edit the data.

```

(the id for $_GET['ID'] is set on the page linking to this one)


<?php
mysql_connect ("localhost", "root","pwordhere")  or die (mysql_error());
mysql_select_db ("pwordlist");

$q = mysql_query("SELECT * FROM PWordTable WHERE ID='".$_GET['id']."'") or die(mysql_error());
?>


<html>
<body>
<form action="edit.php" method="post">
ID: <input type=text name="ID" value="<?php echo $_GET['id']; ?>" size=4 disabled><br>
First name: <input type="text" name="FName" value="<?php echo $_REQUEST['FName']; ?>"/>
<br>
Last name: <input type="text" name="LName" />
<br>
Username: <input type="text" name="UName" />
<br>
Student ID: <input type="text" name="StuID" />
<br>
Category:
<br>
<input type="radio" name="Cat" value="School" >School
<br>
<input type="radio" name="Cat" value="Facebook">Facebook
<br>
<input type="radio" name="Cat" value="MySpace">MySpace
<br>
<input type="radio" name="Cat" value="Other">Other
<br>
<input type="submit" value="submit" />
</form>
</body>
</html> 

```

(edit.php)
```

<?php

mysql_connect ("localhost", "root","pwordhere")  or die (mysql_error());
mysql_select_db ("pwordlist");

      $id = $_GET["ID"];
      $FName = $_POST["FName"];
      $LName = $_POST["LName"];
      $StuID = $_POST["StuID"];
      $UName = $_POST["UName"];
      $Cat = $_POST["Cat"];

      $sql = "UPDATE PWordTable SET FName='$FName',LName='$LName',StuID='$StuID',UName='$UName',Cat='$Cat' WHERE id=$id";

      $result = mysql_query($sql);
      echo "Thank you! Information updated.";
?>

```

Problem is, once I run this code, I get an error

> 
Notice: Undefined index: ID in /opt/lampp/htdocs/database/edit.php on line 6

Notice: Undefined index: Cat in /opt/lampp/htdocs/database/edit.php on line 11

I'm not quite sure why it cannot find Cat or ID, someone else know?

---

### Post by Virtual Liberty on 2009-12-02
[LIST=1]
[*]Use $_GET **OR** $_POST, not both.
[*]Check if $_POST["Cat"] is set and get it's value before executing the query.
[/LIST]

---

### Post by mbeach on 2009-12-02
Before you move on now that you've probably got it working, you may want to read about [sql injection]("http://www.google.com/search?q=sql+injection+php+mysql"). 

Here's the first link from a search:
[http://www.tizag.com/mysqlTutorial/mysql-php-sql-injection.php](http://www.tizag.com/mysqlTutorial/mysql-php-sql-injection.php)

---

### Post by dmillerw on 2009-12-02
> **Virtual Liberty said:**
> [LIST=1]
[*]Use $_GET **OR** $_POST, not both.
[*]Check if $_POST["Cat"] is set and get it's value before executing the query.
[/LIST]
Do you mean change it from GET to POST on the form?

If so, how would I still pass the ID along from the previous page

---

### Post by dmillerw on 2009-12-02
Anybody?

---

### Post by endBc on 2009-12-02
Change the form action to:

```
edit.php?ID=<?php echo $_GET['id']; ?>
```

---

### Post by dmillerw on 2009-12-02
Thanks, that did it

---


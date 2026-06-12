---
title: "using mysql php forms"
date: 2009-07-21
forum: Programming Talk
---

### Post by benh13 on 2009-07-21
I have made a form in php, and want to use a form to get a php file to display all values in a certain price range.

however when i open it up, it comes up with the error message 

**Parse error**:  syntax error, unexpected '"', expecting T_STRING or T_VARIABLE or T_NUM_STRING in **/var/www/test php 2.php** on line **13**

the code for the bit that is causing trouble is
```
mysql_select_db("examples", $con);

$result = mysql_query("SELECT * FROM guitar
 

while($row = mysql_fetch_array($result))
  {
  echo $row['make'] . " " . $row['price'];
  echo "<br/>";
  }
mysql_close($con);
```

line 13 is the bit that says ```
WHERE price<='$_POST["maximum price"]'");
```
if anybody can help it would be great.

---

### Post by Dill on 2009-07-21
Instead of 

```
$result = mysql_query("SELECT * FROM guitar
WHERE price<='$_POST["maximum price"]'");
```

Try

```
$result = mysql_query("SELECT * FROM guitar
WHERE price<='" . $_POST["maximum price"] . "'");
```

The issue has to do with the quotation marks within the brackets in your $_POST variable. Concatenating the $_POST variable, instead, should fix the error.

As an aside, you should check out...

[Using the mysqli extension instead of mysql]("http://us3.php.net/manual/en/mysqli.overview.php")

Cheers,
Dill

---

### Post by Mirge on 2009-07-21
> **benh13 said:**
> I have made a form in php, and want to use a form to get a php file to display all values in a certain price range.

however when i open it up, it comes up with the error message 

**Parse error**:  syntax error, unexpected '"', expecting T_STRING or T_VARIABLE or T_NUM_STRING in **/var/www/test php 2.php** on line **13**

the code for the bit that is causing trouble is
```
mysql_select_db("examples", $con);

$result = mysql_query("SELECT * FROM guitar
 

while($row = mysql_fetch_array($result))
  {
  echo $row['make'] . " " . $row['price'];
  echo "<br/>";
  }
mysql_close($con);
```line 13 is the bit that says ```
WHERE price<='$_POST["maximum price"]'");
```if anybody can help it would be great.

Or changing it to read:

```

WHERE price <= '$_POST[maximum_price]'") or die(mysql_error());

```

would also work.

---


---
title: "php/mysql problem"
date: 2012-12-28
forum: Programming Talk
---

### Post by tehcavil on 2012-12-28
I need to order posts by date. Unfortunately I made the sql table using a varchar(255) type not a timestamp or date type. The date is a string which is the output of date(Y.m.d); Is there any way to sort by date? And is there any way to add time to it as well? am i better off altering the sql table to make the column a "timestamp"? would that be easier to do?

This is what I have currently.

```


<table bgcolor="CDCDCD" border="0" width="100%">
<?php
/* connect to the db */
$connection = mysql_connect('localhost','fencing','y2ZG7bsSZhMbMExR');
mysql_select_db('fencing',$connection);
$result = mysql_query("SELECT * FROM homeposts ORDER BY postid DESC");
while($row = mysql_fetch_array($result))
  {
  echo "<tr><td><h3>" . $row['postdate'] . " | " . $row['postname'] . " - " . "</h3></td></tr><tr><td>" . $row['content'] . "</td></tr><tr><td></td></tr>";
  }
?>
</table>


```

---

### Post by kevinharper on 2012-12-28
You should be able to sort through it. Is 'postid' the column name for where the dates are stored?

I would alter the table so that you have the correct datatype declared. Better now than when that table grows big with records.

---


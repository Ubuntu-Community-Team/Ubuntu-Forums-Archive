---
title: "PHP MySQL query"
date: 2008-06-12
forum: Programming Talk
---

### Post by nonaguy on 2008-06-12
We know how to do a PHP MySQL query:

An example:

<?php
 
$username="";
$password="";
$database="archives";
$id=$_GET['id'];
 
mysql_connect("dataserver.archives.org:3306",$username,$password);
@mysql_select_db($database) or die( "Unable to select database");
$query="SELECT * FROM doctype WHERE ID='$id'";
$result=mysql_query($query);
 
mysql_close();
 
?>

As you can see this puts the results of the query into a variable: $query. What I would like to know is, if it's possible, to run another MySQL query against that variable.

---

### Post by Cypher on 2008-06-12
Actually the results of the query end up in $result and you would use mysql_fetch_xxx on $result to get the values out. You would not use the contents of $result in a query directly. But, you can extract specific infomration from the $result variable and create a new $query to run.

---

### Post by MacAnthony on 2008-06-12
You may also be able to do a subquery so only need to do one database request to accomplish the same

$result = "SELECT * FROM otherTable where docTypeId = (SELECT docTypeId FROM doctype WHERE ID='$id' limit 1)"

So really depends on the structure of the data and what you want to achieve.

---


---
title: "'No element found' error when using Ajax and PHP"
date: 2010-09-06
forum: Programming Talk
---

### Post by resander on 2010-09-06
For Ubuntu 10.04, Apache 2, PHP5 and MySQL 5, Firefox 3.6.
(I already had Apache, Mysql and Firefox installed, so only added PHP5 via synaptic a couple of days ago).  

I have only just started with Ajax and PHP and obtained some demo files from w3school.com (by googling on 'Ajax PHP database') that I named w3.html and getuser.php. These show how to find person details in a MySQL data base and send them back to be displayed by a browser. They work when Firefox accesses the demo at w3schools.com.

I put these files into directory /var/www and tried via Firefox, but got this error showing in the Firefox Error console:

 'Error: no element found
  Source File: file:///var/www/getuser.php?q=1
  Line: 43'

I also obtained a similar demo from [www.tizag.com/ajaxTutorial/ajax-mysql-database.php](www.tizag.com/ajaxTutorial/ajax-mysql-database.php). It failed in the same way, but worked when accessing [www.tizag.com](www.tizag.com) directly. 

I googled on permutations of 'Ajax', 'XMLHTTPRequest' and 'no element found' and noticed that many have had this problem. A few said that this problem occurs when the Ajax-side expects XML but gets HTML from the server, but did not give any solutions.

PHP works when I put 'localhost/getuser.php' into the Firefox addressbar. It generates the captions for the result table that looks well-formed to me. 

Totally stuck. I don't know how to fix this, so would be most grateful for advice.


w3.html
```
 
<html>
<head>
<script type="text/javascript">
function showUser(str)
{
if (str=="")
  {
  document.getElementById("txtHint").innerHTML="";
  return;
  }
if (window.XMLHttpRequest)
  {// code for IE7+, Firefox, Chrome, Opera, Safari
  xmlhttp=new XMLHttpRequest();
  }
else
  {// code for IE6, IE5
  xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
  }
xmlhttp.onreadystatechange=function()
  {
  if (xmlhttp.readyState==4 && xmlhttp.status==200)
    {
    document.getElementById("txtHint").innerHTML=xmlhttp.responseText;
    }
  }
xmlhttp.open("GET","getuser.php?q="+str,true);
xmlhttp.send();
}
</script>
</head>
<body>

<form>
<select name="users" onchange="showUser(this.value)">
<option value="">Select a person:</option>
<option value="1">Peter Griffin</option>
<option value="2">Lois Griffin</option>
<option value="3">Glenn Quagmire</option>
<option value="4">Joseph Swanson</option>
</select>
</form>
<br />
<div id="txtHint"><b>Person info will be listed here.</b></div>

</body>
</html> 

```


getuser.php
```

<?php
ini_set('display_errors', 'On');
error_reporting(E_ALL);

$q=$_GET["q"];

$con = mysql_connect('localhost', 'userid', 'pwd');
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

mysql_select_db("ajaxdemo", $con);

$sql="SELECT * FROM user WHERE id = '".$q."'";

$result = mysql_query($sql);

echo "<table border='1'>
<tr>
<th>Firstname</th>
<th>Lastname</th>
<th>Age</th>
<th>Hometown</th>
<th>Job</th>
</tr>";

while($row = mysql_fetch_array($result))
  {
  echo "<tr>";
  echo "<td>" . $row['FirstName'] . "</td>";
  echo "<td>" . $row['LastName'] . "</td>";
  echo "<td>" . $row['Age'] . "</td>";
  echo "<td>" . $row['Hometown'] . "</td>";
  echo "<td>" . $row['Job'] . "</td>";
  echo "</tr>";
  }
echo "</table>";

mysql_close($con);
?>

```

w3demo.sql to create database ajax_demo, table user and some records.
```

CREATE DATABASE ajax_demo;
USE ajax_demo;

CREATE TABLE user (
  id int, 
  FirstName CHAR(20), 
  LastName  CHAR(20),
  Age int,
  Hometown  CHAR(20),
  Job       CHAR(30)
);
 
INSERT INTO user VALUES
  (1,'Peter','Griffin',41,'Quahog','Brewery');
INSERT INTO user VALUES
  (2,'Lois','Griffin',40,'Newport','Piano Teacher');
INSERT INTO user VALUES
  (3,'Joseph','Swanson',39,'Quahog','Police Officer');
INSERT INTO user VALUES
  (4,'Glenn','Quagmire',41,'Quahog','Pilot');

```

Use mysql command source w3demo.sql from the MySQL command line.

---


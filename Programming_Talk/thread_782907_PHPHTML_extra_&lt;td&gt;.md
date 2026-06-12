---
title: "PHP/HTML extra &lt;td&gt;"
date: 2008-05-05
forum: Programming Talk
---

### Post by kingpoiuy on 2008-05-05
Hello, I am trying to display a table from MySQL on a web page using PHP.  For some reason my table is creating extra <td>'s.  It seems that i can select all the column's and it will display fine but if I skip the 'user' column then the next column after that is blank.  I can post screenshots if necessary.  Here is my PHP website code.

```
<?php
include 'config.php';
include 'opendb.php';
include 'serialdbindex.php';

$query = "SELECT ";


echo "<table border='1' align='center'>";
echo "<tr>";
echo "<td><b>Computer</b></td>";
if($_POST['user'] == 'on')
	{
	$query .= "user, ";
	echo "<td><b>User</b></td>";
	}

if($_POST['windows'] == 'on')
	{
	$query .= "windows, ";
	echo "<td><b>Windows</b></td>";
	}

if($_POST['office'] == 'on')
	{
	$query .= "office, ";
	echo "<td><b>Office</b></td>";
	}

if($_POST['antivirus'] == 'on')
	{
	$query .= "antivirus, ";
	echo "<td><b>Anti-Virus</b></td>";
	}

if($_POST['description'] == 'on')
	{
	$query .= "description, ";
	echo "<td><b>Description</b></td>";
	}

echo "</tr>";

$query .= "computer FROM main ORDER BY computer";
$result = mysql_query($query) or die('Error, query failed');

while($row = mysql_fetch_array($result))
	{
	echo "<tr>";
	echo "<td>" . $row['computer'] . "</td>";
	echo "<td>" . $row['user'] . "</td>";
	echo "<td>" . $row['windows'] . "</td>";
	echo "<td>" . $row['office'] . "</td>";
	echo "<td>" . $row['antivirus'] . "</td>";
	echo "<td>" . $row['description'] . "</td>";
	echo "</tr>";
	}
echo "</table>";
/*
echo "<pre>";
echo $query;
echo "</pre>";
*/
include 'closedb.php';
?>
```

Thank you for looking.

---

### Post by smartbei on 2008-05-05
Unless I am misunderstanding what you are trying to do, the problem is that you are creating the data rows (the while...) regardless of the users choice of whether to display the columns.

Try adding another if block inside the while, so that if the user has not selected to view a certain column they won't see its data.

Some other tips: use <th> for table headers - then you don't need the <b>

---

### Post by kingpoiuy on 2008-05-05
Wonderful I will give thoes things a try and report back.  I'm a noob to php and MySQL so any advice is greatly appreciated.

---

### Post by kingpoiuy on 2008-05-05
Oh yeah, Works like a charm!  Thank you!

---


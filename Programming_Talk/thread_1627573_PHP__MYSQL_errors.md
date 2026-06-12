---
title: "PHP / MYSQL errors"
date: 2010-11-21
forum: Programming Talk
---

### Post by v1ad on 2010-11-21
trying to create this project for knowledge purposes. and i am running into an error which says.

Warning: mysqli_num_rows() expects parameter 1 to be mysqli_result, boolean given in /var/www/team_ur/createorder.php on line 41

tried everything and still not sure what i am doing wrong, prob a stupid mistake that i am overlooking.

here is my script:
[http://paste.ubuntu.com/534991/](http://paste.ubuntu.com/534991/)

```

<?php
/*
Vladimir Gusar
Lab 12
*/
require('header.inc');
?>
<head>
<title>View Customers</title>
</head>
<body>
<div id="banner">
<?php
my_header("Final");
?>
</div>
<?php
session_check();
require('navigation.inc');
?>
<div id="main">
<h1>Orders</h1>
<?php
if (!isset($_POST['submit'])){
	$db = open_db();
	$query = "select * from customers";
	$result = $db->query($query);
	?>
<form action="add_customers.php" method="post">
<p align="center">
<!-- Set up the header for the table -->
<table border="1">
<tr bgcolor="#cccccc">
<td width="100">First Name</td>
<td width="100">Last Name</td>
<td width="100">Sales Total</td>
</tr>
<?php
	$num_results = $result->numRows();
	if ($num_results == 0) {
		echo "<tr>";
		echo '<td>test1</td>';
		echo '<td>test2</td>';
		echo '<td>0.00</td>';
		echo "</tr>";
		echo"</table>";	
	}
	else {
		for ($i=0; $i < $num_results; $i++) {
			$row = mysqli_fetch_row($result);
			echo "<tr>";
			echo "<td>".stripslashes($row[0])."</td>";
			echo "<td>".stripslashes($row[1])."</td>";
			echo "<td>".stripslashes($row[2])."</td>";
			echo "</tr>";
			echo"</table>";
		}
	}
	mysqli_close($db);	
}
else {
		
}

?>
</p>
</div>
</div>
</body>
</html>

```

---

### Post by v1ad on 2010-11-21
bump...

---


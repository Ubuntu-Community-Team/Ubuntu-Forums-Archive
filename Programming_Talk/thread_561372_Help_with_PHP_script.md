---
title: "Help with PHP script"
date: 2007-09-27
forum: Programming Talk
---

### Post by dhtseany on 2007-09-27
Hey all, can someone check my code for me? What is supposed to happen is this page first queries mysql for the pictures names and builds a gallery off of returned results. The problem is when I click the delete link it doesn't remove the mysql data. I hope this is simple.

Thanks,
Sean

```



<?php
 //Secured PHP Start//
 session_start();
if (!isset($_SESSION['db_is_logged_in']) 
	|| $_SESSION['db_is_logged_in'] !== true) {

   // not logged in, move to login page
   header('Location: ../secure/login.php');
   exit;
}
require('../secure/ext_auth.php');
 //Secured PHP End //

$sql = "SELECT *
              FROM upload2
			  	ORDER BY ID desc";

      $result = mysql_query($sql)
                or die('Error, get album info failed. ' .
                        mysql_error());


echo '<center><p><a href="http://www.myaiw.com/secure/main.php">CPanel Home</a> | <a href="http://www.myaiw.com">MyAIW Home</a></p><table width="95%" border="0" cellspacing="5" cellpadding="2" align="center">';

$colsPerRow = 4;

// width of each column in percent
$colWidth = (int)(75/$colsPerRow);

while ($row = mysql_fetch_assoc($result)) {
   if ($i % $colsPerRow == 0) {
      // start a new row
      echo '<tr>';
   }
   $numImages = $row['id'] > 1 ?
                $row['id'] . ' images'
                : $row['id'] . ' image';

   echo '<td width="' . $colWidth . '%" align="center">' .
        '<a href="http://www.myaiw.com/upload/' . $row['name'] . '"><img src="http://www.myaiw.com/upload/thumb_' . $row['name'] . '"></a><br>' . 
		'<a href="auth_view.php?file=' . $row['name'] . '&thumb=thumb_' . $row['name'] . '&sqlid=' . $row['name'] . '">Delete</a>';

   if ($i % $colsPerRow == $colsPerRow - 1) {
      // end this row
      echo '</tr>';
   }

   $i += 1;
}


// print blank columns
if ($i % $colsPerRow != 0) {
   while ($i++ % $colsPerRow != 0) {
      echo '<td width="' . $colWidth . '%">&nbsp;</td>';
   }
   echo '</tr>';
}

echo '</table>';

//Image Delete Code//
$SQLDEL = "delete from upload2 where name = '".mysql_real_escape_string($_GET['sqlid'])."'";

if(isset($_GET['file'])){
unlink($_GET['file']);
}
if(isset($_GET['thumb'])){
unlink($_GET['thumb']);
}
if(isset($_GET['sqlid'])){
$result = mysql_query($sql) or die(mysql_error());
}
					
echo "File has been deleted. Click <a href='http://www.myaiw.com/upload/index.php'>here</a> to continue."; 
?>

```

---

### Post by diggity on 2007-09-27
You're not running the delete sql anywhere in your code.
You need **mysql_query($SQLDEL);** in order to execute the delete sql statement.

---

### Post by dhtseany on 2007-09-27
That was a mistake on my part; I meant to change that.

However, the query returns an error stating "Query is empty."

Any ideas? I'm guessing it's because the query isn't getting the correct result injected before the query is run.

---

### Post by dhtseany on 2007-09-27
*bump* :)

---


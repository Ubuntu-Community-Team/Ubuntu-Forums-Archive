---
title: "mysql php working example for submit, want to add paging"
date: 2011-01-14
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-14
can someone take a look at this?
this displays all the results into a table
but would like to display a range with some kind of forward and reverse button.

```
<html>
<head>
<basefont face="Arial">
</head>
<body>

<?php

if (!isset($_POST['submit'])) {
// form not submitted
?>

    <form action="<?=$_SERVER['PHP_SELF']?>" method="post">
    Title: <input type="text" name="btitle">
    Author: <input type="text" name="bauthor">
    <input type="submit" name="submit">
    </form>

<?php
}
else {
// form submitted
// set server access variables
    $host = "localhost";
    $user = "root";
    $pass = "New";
    $db = "booksgood";
    $max_results = 5; /// Number of results per page
   
// get form input
    // check to make sure it's all there
    // escape input values for greater safety
    //look for blank input and reject
    //$btitle = empty($_POST['btitle']) ? : mysql_escape_string($_POST['btitle']);
    //$bauthor = empty($_POST['bauthor']) ? : mysql_escape_string($_POST['bauthor']);
    
    //just escape the input '
    $btitle =  mysql_escape_string($_POST['btitle']);
    $bauthor = mysql_escape_string($_POST['bauthor']);
    
    //just take the input
    //$btitle = ($_POST['btitle']);
    //$bauthor =($_POST['bauthor']);

    // open connection
    $connection = mysql_connect($host, $user, $pass) or die ("Unable to connect!");
    
    // select database
    mysql_select_db($db) or die ("Unable to select database!");       
    
   // print $btitle;
   // print $bauthor;

// create query
IF (empty($btitle)) 
  {
  $query = "SELECT titles, author FROM bookdata where  author like '$bauthor%'";
  $totals = mysql_result(mysql_query("SELECT COUNT(id) FROM bookdata where author like '$btitle%'"),0);
  }
ELSEIF (empty($bauthor)) 
  {
   $query = "SELECT titles, author FROM bookdata where titles like '$btitle%'";
   $totals = mysql_result(mysql_query("SELECT COUNT(id) FROM bookdata where titles like '$btitle%'"),0);
  }
ELSE
  {
   $query = "SELECT titles, author FROM bookdata where titles like '$btitle%' and author like '$bauthor%'";  
   $totals = mysql_result(mysql_query("SELECT COUNT(id) FROM bookdata where titles like '$btitle%' and author like '$bauthor%'"),0);   
  } 

  //   print $query;
   /// START of MySQL results – Page numbering
   /// Count total
   
    // this works
    // $totals = mysql_result(mysql_query("SELECT COUNT(id) FROM bookdata"),0);      
    // $totals = mysql_result(mysql_query("SELECT COUNT(id) FROM bookdata where titles like 'a%'"),0);        


   $total_pgs = ceil($totals / $max_results);

  // print $query2;
  // print $totals;
  // print $total_pgs;
   

 
   // execute $query
   $result = mysql_query($query) or die ("Error in query: $query. ".mysql_error());

  
   //determine number of rows
   // $totalls = mysql_num_rows($result);

// see if any rows were returned
if (mysql_num_rows($result) > 0)
    {
    // yes
    // print them one after another
    echo "<table cellpadding=10 border=1>";
    while($row = mysql_fetch_row($result))
    {
        echo "<tr>";
        echo "<td>".$row[0]."</td>";
        echo "<td>".$row[1]."</td>";
        echo "<td>".$row[2]."</td>";
        echo "<td>".$row[3]."</td>";
        echo "</tr>";
    }
    echo "</table>";
    }
else 
    {
    // no
    // print status message
    echo "No results found!";
    }

// free result set memory
mysql_free_result($result);



    // close connection
    mysql_close($connection);

} //last curly comes from top if submit else statement
?>

</body>
</html>
```

---


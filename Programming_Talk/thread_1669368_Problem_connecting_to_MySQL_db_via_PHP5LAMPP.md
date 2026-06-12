---
title: "Problem connecting to MySQL db via PHP5/LAMPP"
date: 2011-01-17
forum: Programming Talk
---

### Post by fblevins on 2011-01-17
Unsure what's going on here as the code looks good (admittedly I've been away from programming for awhile though).

I'm using LAMPP from [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) and PHP5. Created a tiny little db with 6 recs in one table and am trying to connect to it and display it's contents via PHP. To wit:

<html>
<body>

<?php

$username = 'root';
$userpass = '';
$hostname = 'localhost'; 

$dbhandle = @mysql_connect($hostname, $username, $uerpass) 
  or die('Unable to connect to MySQL'); 
echo 'Connected to MySQL<br>'; //Connected to MySQL

$result = mysql_query('select * from Uses');
if (!$result)
	echo 'false';
else
	echo $result; //Returns false

?>

</body>
</html>

I don't believe this is a permissions problem as I have no username or pw set. I've checked phpinfo() after this script runs and show an active connection, I'm just not able to get to the table. Any ideas?

---

### Post by sdowney717 on 2011-01-17
how about the password field being blank?

> 
    // set server access variables
    $host = "localhost";
    $user = "root";
    $pass = "New";
    $db = "booksgood";

    // open connection
    $connection = mysql_connect($host, $user, $pass) or die ("Unable to connect!");
    
    // select database
    mysql_select_db($db) or die ("Unable to select database!"); 

 






---

### Post by sdowney717 on 2011-01-17
are you able to connect?
have you selected the database to use?

---

### Post by fblevins on 2011-01-17
> **sdowney717 said:**
> how about the password field being blank?

The generic install of LAMPP is root and no password. I've tried with no password param being passed, a blank pw and with "New" same results every time.

When running

$dbhandle = @mysql_connect($hostname, $username, $uerpass) 
  or die('Unable to connect to MySQL'); 
echo 'Connected to MySQL<br>'; //Connected to MySQL
echo $dbhandle;

my browser returns "Resource id #3" so I assume I'm connecting to the db, but anything thereafter (like select, list tables, etc. is kaput). Am I failing to connect to a specific database within MySQL?

---

### Post by sdowney717 on 2011-01-17
Am I failing to connect to a specific database within MySQL?

yes, you need to select a database to use by using mysql_select_db


$db = "booksgood";
// select database
mysql_select_db($db) or die ("Unable to select database!");

---

### Post by fblevins on 2011-01-17
> **sdowney717 said:**
> are you able to connect?
have you selected the database to use?

Got it with

<?php

$username = 'root';
$userpass = '';
$hostname = 'localhost'; 

$dbhandle = @mysql_connect($hostname, $username, $uerpass) 
  or die('Unable to connect to MySQL'); 
echo 'Connected to MySQL<br>'; //Connected to MySQL
echo $dbhandle;

$database = mysql_select_db('EssentialOils',$dbhandle);

$result = mysql_query('select * from Uses',$dbhandle);
if (!$result)
	echo 'false';
else
	echo $result; //Returns false

while ($row = mysql_fetch_assoc($result)) {
    echo $row['Use'];
}

?>

You were spot on. After making your MySQL connection you STILL have to select a database to work with (DUH)!!! I told ya'll it'd been awhile since I'd done this!

Thanks for all the help!!!

---

### Post by sdowney717 on 2011-01-17
glad you got it.

I noticed your using the connection handle. I found you dont need it, so what is the advantage? 

$dbhandle = @mysql_connect($hostname, $username, $uerpass) 
$database = mysql_select_db('EssentialOils',$dbhandle);
$result = mysql_query('select * from Uses',$dbhandle);


I found this works, is the $connection just there by default?
as in it knows what the connection made is, or would this be important if you were opening multiple connections to the database at the same time?

// set server access variables
    $host = "localhost";
    $user = "root";
    $pass = "New";
    $db = "booksgood";

 // open connection
    $connection = mysql_connect($host, $user, $pass) or die ("Unable to connect!");
    
    // select database
    mysql_select_db($db) or die ("Unable to select database!");  
 // execute $query
    $result = mysql_query($query) or die ("Error in query: $query. ".mysql_error());


I also run this when it is done.
> // free result set memory
mysql_free_result($result);



    // close connection
    mysql_close($connection);

---

### Post by fblevins on 2011-01-17
> **sdowney717 said:**
> glad you got it.

I noticed your using the connection handle. I found you dont need it, so what is the advantage? 

$dbhandle = @mysql_connect($hostname, $username, $uerpass) 
$database = mysql_select_db('EssentialOils',$dbhandle);
$result = mysql_query('select * from Uses',$dbhandle);


I found this works, is the $connection just there by default?
as in it knows what the connection made is, or would this be important if you were opening multiple connections to the database at the same time?

// set server access variables
    $host = "localhost";
    $user = "root";
    $pass = "New";
    $db = "booksgood";

 // open connection
    $connection = mysql_connect($host, $user, $pass) or die ("Unable to connect!");
    
    // select database
    mysql_select_db($db) or die ("Unable to select database!");  
 // execute $query
    $result = mysql_query($query) or die ("Error in query: $query. ".mysql_error());


I also run this when it is done.

The $database was an artifact from testing to see if I was getting a resource reference back from the call. I took that out now that everything seems to be working. Thanks for catching that and also reminding me that I need to RELEASE all my db stuff at end of script!

---


---
title: "Some problems with Zpanel..."
date: 2009-08-04
forum: Programming Talk
---

### Post by Surd on 2009-08-04
Couldn't find anywhere else to put this, So Development seemed ok at the time. Anyway, Just installed Zpanel 2.5 using all the instructions, Chmoding and everything else. All the details are correct but there is one problem. The index.php file and all the other links think I am trying to hack my own website. I tempoarily removed the anti-hack code and saw it was something to do with the auth.php file not connecting to the database. I have tried putting ```
include("mysql.php")
```in to no avail. ([http://dhnet.co.uk/dpanel](http://dhnet.co.uk/dpanel)) That is the homepage with the problem you can see. Any help would be appreceated, I need to try and sort this out sooner rather than later as I have spent hundreds of £'s on eqipment for my hosting company, but no customers.
 
Cheers,
Conor
[SIZE=1]DeltaHost Networks[/SIZE]

---

### Post by Surd on 2009-08-04
Ps. Here are the key files...
mysql.php
[php] 
<?php
 
 
// ZPanel auto-generated config file
// Do not change anything in this file!
 
if (isset($zpaneldirectory)) {
if ($_SERVER['PHP_SELF'] != 'mysql.php') {
$cwd = strtolower(str_replace('\\', '/', getcwd()));
$zpdir = strtolower(str_replace('\\','/',$zpaneldirectory));
$zpcount = strlen($zpdir);
if (substr($cwd, 0, $zpcount) == $zpdir) {
 
$db_host = 'localhost';
$db_name = 'dpanel';
$db_user = 'root';
$db_pass = 'my_sql_password';
 
}else{
die ('Hacking Attempt - ID #3'); }
}else{
die ('Hacking Attempt - ID #2'); }
}else{
die ('Hacking Attempt - ID #1');
}
?>
[/php]
 
[SIZE=1]auth.php[/SIZE]
[php]
<?php
 
$db_engine = 'mysql';
$db_object = mysql_pconnect($db_host, $db_user, $db_pass) or die(mysql_error());
$database_Customer_Database = $db_name;
$Customer_Database = mysql_pconnect($db_host, $db_user, $db_pass) or die(mysql_error());
$colname_Config = "1";
mysql_select_db($database_Customer_Database, $Customer_Database);
$query_Config = sprintf("SELECT * FROM config", $colname_Config);
$Config = mysql_query($query_Config, $Customer_Database) or die(mysql_error());
$row_Config = mysql_fetch_assoc($Config);
 
$totalRows_Config = mysql_num_rows($Config);
$db_engine = 'mysql';
$db_object = mysql_pconnect($db_host, $db_user, $db_pass) or die(mysql_error());
$database_MySQL = "mysql";
$MySQL = mysql_pconnect($db_host, $db_user, $db_pass) or die(mysql_error());
 
if (isset($_SESSION['username'])) {
    mysql_select_db($database_Customer_Database, $Customer_Database);
    $query_User = sprintf("SELECT * FROM custumerbase WHERE servicename = '".$_SESSION['username']."'");
    $User = mysql_query($query_User, $Customer_Database);
    $row_User = mysql_fetch_assoc($User);
    $totalRows_User = mysql_num_rows($User);
}
 
?>
[/php]

---

### Post by Surd on 2009-08-05
Dont know how, I deleted the Apache conf file for the panel and moved it to my main site as a subdir, it works now. Problem solved!

---


---
title: "PHP Search function"
date: 2011-07-28
forum: Programming Talk
---

### Post by Kyluke on 2011-07-28
Hey I have a website with a mysql database.

Now I need to have a search function built in but for some reason my code only ever produces either the first line (no matter what) or the whole table.

Here is my code and i want it to return only one row with the correct data

[PHP]<?php
mysql_connect ("localhost", "chaos_theory","12345")  or die (mysql_error());
mysql_select_db ("students");
 
$term = $_GET['student_number'];
 
$sql = mysql_query("select * from students where student_number like '%$term%'");
 
while ($row = mysql_fetch_array($sql)){
    echo 'ID: '.$row['id_number'];
    echo '<br/> First Name: '.$row['student_number'];
    echo '<br/> Last Name: '.$row['first_name'];
    echo '<br/> Phone: '.$row['surname'];
    echo '<br/><br/>';
    }
 
?>[/PHP]

---

### Post by hooflung64 on 2011-07-28
Try:

[PHP]
<?php
mysql_connect ("localhost", "chaos_theory","12345")  or die (mysql_error());
mysql_select_db ("students");
 
$term = $_GET['student_number'];

$query = sprintf("SELECT * from students where student_number like '%s'",
    mysql_real_escape_string($term);
 
$result = mysql_query($query);
 
while($row = mysql_fetch_assoc($result)) 
    echo 'ID: '.$row['id_number'];
    echo '<br/> First Name: '.$row['student_number'];
    echo '<br/> Last Name: '.$row['first_name'];
    echo '<br/> Phone: '.$row['surname'];
    echo '<br/><br/>';
    }
 
?> 
[/PHP]

If that doesn't provide any different of outcome then you need to revisit your query. Possibly run it on the cli client for mysql until you get the desired results.

---

### Post by Kyluke on 2011-07-29
[COLOR=#000000] [/COLOR]> [PHP]<?php
mysql_connect ("localhost", "chaos_theory","12345")  or die (mysql_error());
mysql_select_db ("students");
 
$term = $_GET['student_number'];
 
$sql = mysql_query("select * from students where student_number like '%$term%'");
 
while ($row = mysql_fetch_array($sql)){
    echo 'ID: '.$row['id_number'];
    echo '<br/> First Name: '.$row['student_number'];
    echo '<br/> Last Name: '.$row['first_name'];
    echo '<br/> Phone: '.$row['surname'];
    echo '<br/><br/>';
    }
 
?>[/PHP]

This doesn't work, the site does not even open, I will try to figure out why. The sql queries run fine in cli
[COLOR=#000000] [/COLOR]

---

### Post by Kyluke on 2011-07-29
Got it working

---


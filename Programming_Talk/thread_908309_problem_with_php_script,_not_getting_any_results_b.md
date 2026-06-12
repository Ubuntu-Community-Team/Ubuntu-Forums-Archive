---
title: "problem with php script, not getting any results back"
date: 2008-09-02
forum: Programming Talk
---

### Post by Mia_tech on 2008-09-02
I have a script that basically queries the db and puts the result back on the page, but I'm not getting anything back nor any errors so I created a simple connection script to see if I was able to connect and I got "Resource id #1"
the code to test the connection
[PHP]<?php
$conn = mysql_connect("localhost", "root", "password") or die(msyql_error());
mysql_select_db("test",$conn) or die(msyql_error());
echo "$conn";     
?> [/PHP]

but when I use the real script I'm not getting anything back.. here's the script
[PHP]<?php
$conn = mysql_connect("localhost", "root", "password") or die(msyql_error());
msyql_select_db("test",$conn) or die(mysql_error());
$sql = "select * from members";
$result = mysql_query($sql,$conn);
while ($data = mysql_fetch_array($result)) {
    $username = $data[username];
    $password = $data[password];
    $msg = $username $password;
    }
?>
<html>
<body>
<?php print $msg; ?>
</body>
</html>
[/PHP]

---


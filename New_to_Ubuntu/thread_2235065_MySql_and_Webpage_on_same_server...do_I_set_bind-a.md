---
title: "MySql and Webpage on same server...do I set bind-address to 127.0.0.1?"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by adrian33 on 2014-07-18
I am writing my first PHP code. The goal is simple.....display query results in a table. 

In the my.cnf file, I commented out all of my bind-address lines and can access my database remotely (using a managed DNS) using MySQL Workbench. Now I would write a php file that will display data. Since  both the php file and the MySQL database are on the same server, should I change my.cnf to contain bind-address = 127.0.0.1?  Should I use bind-address= '%'?  Should I use bind-address = 'MyDNSAlias.com'  ALL?  NONE?  I would like to maintain the ability to access the database remotely but am under the assumption that using localhost, if able, is faster.

So far, my Code is not working

```

<?php$username="username";$password="password";
$database="your_database";mysql_connect(localhost,$username,$password);
@mysql_select_db($database) or die( "Unable to select database");
$query="SELECT * FROM tablename";$result=mysql_query($query);
$num=mysql_numrows($result);mysql_close();
echo "<b>
<center>Database Output</center>
</b>
<br>
<br>";
$i=0;while ($i < $num) {$field1-name=mysql_result($result,$i,"field1-name");
$field2-name=mysql_result($result,$i,"field2-name");
$field3-name=mysql_result($result,$i,"field3-name");
$field4-name=mysql_result($result,$i,"field4-name");
$field5-name=mysql_result($result,$i,"field5-name");
echo "<b>
$field1-name $field2-name2</b>
<br>
$field3-name<br>
$field4-name<br>
$field5-name<hr>
<br>";$i++;}?>

```

---

### Post by SeijiSensei on 2014-07-18
It might be trivially faster to use localhost, but if you want to enable remote connections, MySQL needs to be bound to a network interface.  Just use the corresponding hostname or IP address instead of localhost in mysql_connect().

Alternatively you could use
```
bind-address = *
```
which enables connections to MySQL on all interfaces including both localhost and the network interfaces.  

If this is a public server, you need to ensure that only legitimate connections are permitted.  You can do this with the 'user'@'host' account names in MySQL, but I'd recommend using iptables to block all connections to port 3306 that do not come from known addresses, or use a VPN to connect and only enable that and localhost.

---

### Post by adrian33 on 2014-07-18
Thank you. That was very helpful!

Adrian

---


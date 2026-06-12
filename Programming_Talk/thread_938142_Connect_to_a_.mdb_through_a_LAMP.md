---
title: "Connect to a .mdb through a LAMP"
date: 2008-10-04
forum: Programming Talk
---

### Post by soluphobe on 2008-10-04
I'm running Ubuntu 8.04 Desktop, and I installed all the LAMP packages on it. Unfortunately, I need to connect to an mdb file and there have been problems.  I've installed mdbtools, libmdbtools, libmdbodbc, unixodbc-bin, and probably a few others.  PHP parses correctly, so that doesn't seem to be the problem.  However, I get an error when I view this page:

[PHP]<html>
<body>
<?php
  $conn=odbc_connect('SONGS','','');
  if (!$conn)
  {
    exit("Connection Failed: " . $conn);
  }
  $sql="SELECT * FROM Music";
  $rs=odbc_exec($conn,$sql);
  ...[/PHP]

I get:

**Fatal error:** Call to undefined function odbc_connect() in **/var/www/database_test.php** on line **4**

I'm very new to experimenting with servers - I just got the setup working a few days ago.  Can someone point me in the direction of some config file or command that I can use to force php to recognize the odbc functions?  I remember hearing something about the /etc/php5/apache2/php.ini file, but I don't want to touch it without knowing what I'm doing.

Thanks.

---


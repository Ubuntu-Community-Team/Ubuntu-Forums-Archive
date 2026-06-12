---
title: "Using Php to Start/Stop daemon in ubuntu server"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by termvrl on 2013-05-11
Hi All,

i am install a apache, mysql server in ubuntu 12.04.
what i try to do, using a php code to start/stop mysql daemon.

here my code,

<html>
<body>

<?php
exec("sudo /etc/init.d/mysql start > /dev/null 2>&1 &");
?>
</body>
</html> 

when i do ps aux, mysql not running... when i try to use phpadmin console also cannot login.

thanks

---


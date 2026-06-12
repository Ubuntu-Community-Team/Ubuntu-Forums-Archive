---
title: "OS command in php"
date: 2005-07-29
forum: Programming Talk
---

### Post by KrisDwyer on 2005-07-29
Hey,

Just Out of interest is there a command that prints what os you are running? Just interested... 

Kris

---

### Post by dave9191 on 2005-07-29
Well you could try printing out the enviromental varible "TERM". 

Or you can run a shell command "uname -a". 

Dave

---

### Post by TomB on 2005-07-29
<?php echo system("uname -a"); ?>

---

### Post by dare2dreamer on 2005-07-29
[http://us3.php.net/manual/en/function.exec.php](http://us3.php.net/manual/en/function.exec.php)

Just remember that the web server runs as its own user, so you'll need to make sure whatever applications you want to run have appropriate permissions. (A potential security risk)

I build a headless server at one point which allowed a web page to shut down and reboot the server, I gave user www-data sudo permissions with no password on one command, /usr/sbin/shutdown.

see man sudoers for details.

---

### Post by odyniec on 2005-07-30
Try php_uname().

[http://www.php.net/manual/en/function.php-uname.php](http://www.php.net/manual/en/function.php-uname.php)

---


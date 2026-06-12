---
title: "Test PHP program"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by zebmustafa2010 on 2013-11-23
Hi,
I want to check whether my LAMP server is successfully running and install , for this I write a code using terminal given below:-
First open the .php file by this command
**sudo  editor/ var/www/test.php**
Then write php code in it
<html>
<head>
<title>Test PHP Programe</title></head>
</head>
<body>
<?php echo 'Hello word !' ?>
</body>
</html>

After that I browse the URL:"**[http://localhost]("http://localhost/test.php")**". Message display on web page given below
**[SUP][SIZE=1]"[/SIZE][/SUP]It works!**
 This is the default web page for this server.
 The web server software is running but no content has been added, yet."

When browse URL:"**[http://localhost]("http://localhost/test.php")/test.php" **for test the file name test.php
The page is blank , it show nothing.
need help!

---

### Post by slpitts on 2013-11-23
What version of Ubuntu are you running? Have you verified that the PHP Apache module has been installed and enabled? 

Quick check would be to scan /var/log/apache2/error.log and confirm that Apache is reporting PHP is configured, should look something
like: Apache/2.4.6 (Ubuntu) PHP/5.5.3-1ubuntu2 configured -- resuming normal operations

If Apache does not have the PHP module enabled you can enable it by using the command: *sudo a2enmod php5*
[FONT=Ubuntu Mono]After enabling the PHP module you'll need to restart Apache with the command: [/FONT]*sudo service apache2 restart*

Your test.php file can be minimal, just contain the line: **<?php phpinfo(); ?>**
Place test.php in your webroot directory and call your test page via browser at: [http://localhost/test.php](http://localhost/test.php)

---


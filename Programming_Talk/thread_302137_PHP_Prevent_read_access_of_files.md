---
title: "PHP: Prevent read access of files?"
date: 2006-11-18
forum: Programming Talk
---

### Post by haaglin on 2006-11-18
Hi.

Not sure if this is a programming issue or server issue, but
i'm looking for a good way of protecting my config files that contains mysql passwords from being read by other customers on the same host as i use. As a test i made a config file, and uploaded it on my user. And i used another account to upload a script to read the file.
To explain further, here is an example:

[www.domain1.com:](www.domain1.com:)
Code:

root: /var/www/web1/web/
file: /var/www/web1/web/config/constants.php
constants.php:
```
<?
define("MYSQL_PASS","123456789");
?>
```

[www.domain2.com:](www.domain2.com:)

root: /var/www/web2/web/
file: /var/www/web2/web/test.php
test.php:
```

<?php
$filename = realpath("../../web1/web/config/constants.php");
$handle = fopen($filename, "r");
$contents = fread($handle, filesize($filename));
fclose($handle);
echo '<textarea name="textareaName" rows="46" cols="103">'.$contents.'</textarea>';
?>
```

And i was able to read the file? Is this a host security issue? or can i do something to prevent reading?

I tried to deny world read access, but then apache didn't have access to it. This is a huge security issue for me.

---

### Post by Miademora on 2006-11-18
It is a host configuration usually.

[http://de.php.net/features.safe-mode](http://de.php.net/features.safe-mode)

for example: open_basedir

---

### Post by haaglin on 2006-11-18
Thanks for clearing this up for me.

---

### Post by snakdoc on 2009-04-15
i tend to put file one dir back 

[www.domain1.com:](www.domain1.com:)
Code:

root: /var/www/web1/web/
file: /var/www/web1/web/config/constants.php
constants.php:

would be /var/www/web1/constants.php

then code that calls that file would be 

../constants.php

---

### Post by drubin on 2009-04-15
> **haaglin said:**
> 
And i was able to read the file? Is this a host security issue? or can i do something to prevent reading?

I tried to deny world read access, but then apache didn't have access to it. This is a huge security issue for me.

If this is shared hosting? This is a huge security risk and I suggest reporting this to them and changing hosts.

Each user should only have read access to their own files and the webserver should be configured as such.

---

### Post by snakdoc on 2009-04-15
you should be able to chmod file in ftp client most support that

---

### Post by drubin on 2009-04-16
> **snakdoc said:**
> you should be able to chmod file in ftp client most support that

This has nothing to do with preventing the webserver from reading files in other vhosts. The standard setup of apache/most webservers runs as a single user and that user normally needs read access to your scripts. If you remove the group/other access rights the webserver might not be able to read it.

The solution is to lockdown each vhost from reading each others. There are other types such as suphp and open_basedir. This is a server config and nothing that can befixed by chmoding files.

as said before this i a hosting provider issue. (Who ever is doing it)

EDIT: I just read the starting date of this OP's first post. This thread was started over 2 years ago. If snakdoc you require any assistance or such please start your own thread. I am sorry for carrying on with outdated threads.

---


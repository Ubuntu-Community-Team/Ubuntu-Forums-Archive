---
title: "php pear installation"
date: 2010-01-15
forum: Programming Talk
---

### Post by sulekha on 2010-01-15
Hi all,

I was attempting the pear installation as per the instructions given here:-

[https://help.ubuntu.com/community/PhpPear](https://help.ubuntu.com/community/PhpPear)

 I think i got the installation correct.

Then i tried this program 

<?php

require_once 'System/Folders.php';
$sf = new System_Folders();
$home = $sf->getHome();
echo "$home\n";

?>

and compiled it as follows:- 

php spear.php

to get the results as

Warning: require_once(System/Folders.php): failed to open stream: No such file or directory in /var/www/spear.php on line 3

Fatal error: require_once(): Failed opening required 'System/Folders.php' (include_path='.:/opt/ZendFramework/current/library:/usr/share/php5:/usr/share/pear') in /var/www/spear.php on line 3


how should i correctly set the path in /etc/php5/apache2/php.ini


or how correct is my path statement

include_path = ".:/opt/ZendFramework/current/library:/usr/share/php5:/usr/share/pear"

in   /etc/php5/apache2/php.ini

---

### Post by Hellkeepa on 2010-01-15
HELLo!

Did you run the following command, and made sure that the "include_path" in "php.ini" is set correctly? Remember to restart your web browser after making the changes.
```
pear list-files System_Folders
```
If you have, please provide us with the output so that we can see if there is anything wrong here.

Also, you do not compile the PHP script, you're *executing* it. The PHP command is just the CLI parser, which runs through the script (almost) as the web server would do.

Happy codin'!

---

### Post by sulekha on 2010-01-15
zodiac@zodioc:~$ pear list-files System_Folders

Installed Files For System_Folders
==================================
Type Install Path
php  /usr/share/php/System/Folders/Cached.php
php  /usr/share/php/System/Folders.php
doc  /usr/share/php/docs/System_Folders/examples/cached.php
doc  /usr/share/php/docs/System_Folders/examples/example.php

---

### Post by Hellkeepa on 2010-01-15
HELLo!

And there we have the issue. Compare the include path as reported by PHP to what the ouput of the pear command was, and you should spot it for yourself. ;-)

Happy codin'!

---


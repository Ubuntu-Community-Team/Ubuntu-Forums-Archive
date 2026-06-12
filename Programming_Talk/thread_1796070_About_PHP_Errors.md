---
title: "About PHP Errors"
date: 2011-07-03
forum: Programming Talk
---

### Post by adeee on 2011-07-03
Guys am new in PHP. just start learning php.ok my question is when i type any php code and if any error occurs! the error in browser not shown for example in this code.

```
<?php phpinfo() ?>
```the semi collen is missing.
and in output of this code. there are no any syntex error line show. just a blank page appear.

i install php through this [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP). and follow all the instructions. step by step. 

What is the solution?

---

### Post by cgroza on 2011-07-03
Run the script with php from the command line. It should spit out some errors.
```

php your_file.php

```
If you use Firefox, check the error console option from the tools menu.

---

### Post by adeee on 2011-07-03
> **cgroza said:**
> Run the script with php from the command line. It should spit out some errors.
```

php your_file.php

```If you use Firefox, check the error console option from the tools menu.

commindline is fine.
but error console also not working. how to appear the errors any idea?

---

### Post by cgroza on 2011-07-03
Well, this is no longer a PHP problem. It is a browser problem.

I know that Javascript errors show up in the browser's error console.

---

### Post by roccivic on 2011-07-03
Apache handles PHP errors. Open a terminal and execute:

```
sudo gedit /etc/php5/apache2/php.ini
```

Search for "display_errors" directive (it may be there more than once) and set it to "On" in every instance. Then restart apache:

```
sudo /etc/init.d/apache2 restart
```

Rouslan

---

### Post by adeee on 2011-07-04
> **roccivic said:**
> Apache handles PHP errors. Open a terminal and execute:

```
sudo gedit /etc/php5/apache2/php.ini
```Search for "display_errors" directive (it may be there more than once) and set it to "On" in every instance. Then restart apache:

```
sudo /etc/init.d/apache2 restart
```Rouslan

obviously solved it. thanxs dude.

---

### Post by SeijiSensei on 2011-07-04
If you don't turn on display_errors, they'll be logged to /var/log/apache2/error.log (or whatever custom error log you've defined for a virtual host).  Displaying errors in the visible pages opens a security hole for potential attackers, so make sure you turn off display_errors if you put your site in production on a publicly-visible server.

---

### Post by adeee on 2011-07-04
> **SeijiSensei said:**
> If you don't turn on display_errors, they'll be logged to /var/log/apache2/error.log (or whatever custom error log you've defined for a virtual host).  Displaying errors in the visible pages opens a security hole for potential attackers, so make sure you turn off display_errors if you put your site in production on a publicly-visible server.

Well i didnt defined any log file.
and thanxs for the tip. it will be noted.
is localhost is safe for turning on this errors or its also a security problem?

---

### Post by v8YKxgHe on 2011-07-04
On localhost it is obviously OK to enable "display_errors". Also ensure that your "error_reporting" is set to "E_ALL | E_STRICT" within your php.ini file.

Also, the missing semi-colon is perfectly valid PHP syntax since it is the last thing.

```
$ echo "<?php phpinfo() ?>" > phpinfo.php
$ cat phpinfo.php 
<?php phpinfo() ?>
$ php -l phpinfo.php 
No syntax errors detected in phpinfo.php
```

---


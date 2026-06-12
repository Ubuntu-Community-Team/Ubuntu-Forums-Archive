---
title: "Installing php"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by perito on 2008-05-31
I did this
```

sudo apt-get install apache2
sudo apt-get install php5
sudo /etc/init.d/apache2 restart

```
also I tried
```
sudo a2enmod php5

```

I tried it, and it doesnt parse php files.

Instead of that it offers me to download it as a .php file which is not parsed.
whats should i do?

---

### Post by quelx on 2008-05-31
You need the php module for apache.

```
sudo apt-get install libapache2-mod-php5
```

and reload apache

```
sudo /etc/init.d/apache reload
```

if that does not work make sure the **php5** module is enabled

```
sudo a2enmod php5
```

and reload **apache2** again

---

### Post by perito on 2008-05-31
its already installed and the module is enabled...
should the files be in /var/www/ to work?
because when I put them there, it doesnt ask me to download the php file, instead it does nothing at all...

---

### Post by quelx on 2008-05-31
```
nano -w test.php
```

paste this code in

```
<?php

phpinfo();

?>

```

**CTRL-X** to save and quit

```
sudo mv test.php /var/www/
```

open firefox and goto **[http://localhost/test.php](http://localhost/test.php)**

---


---
title: "PHP-GTK2 problem"
date: 2008-02-01
forum: Programming Talk
---

### Post by frankos44 on 2008-02-01
The following php code snippet was fired up by typing:

$ php -f test.phpw

<?php
	if (!class_exists('gtk')) {
		die("Please load the php-gtk2 module in your php.ini\r\n");
	}
?>

I have 3 php.ini files on my system:

/etc/php5/cli/php.ini
/etc/pdp5/cgi/php.ini
/etc/php5/apache2/php.ini

I assume the /etc/php2/cli is the file I need to change. What exactly to I need to add to this file please?

---

### Post by tosk on 2008-02-08
```
extension=php_gtk2.so
```

[http://gtk.php.net/manual/en/tutorials.installation.linux.php](http://gtk.php.net/manual/en/tutorials.installation.linux.php)

See near the bottom where it says 'Testing Your Installation.'

---

### Post by frankos44 on 2008-02-08
Thanks for that, it worked a treat. Now i can write my php snippet instead of firing up a web page every time.

---


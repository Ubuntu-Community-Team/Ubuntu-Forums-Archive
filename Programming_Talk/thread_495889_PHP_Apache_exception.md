---
title: "PHP Apache exception"
date: 2007-07-08
forum: Programming Talk
---

### Post by SwaroopKunduru on 2007-07-08
Hi every one,

Fatal error: [COLOR="Red"]Smarty error: unable to write to $compile_dir '/var/www/smarty/templates_c'. Be sure $compile_dir is writable by the web server user. in /usr/local/lib/php/Smarty/Smarty.class.php on line 1095[/COLOR]

I am getting above error. I am running a php file with template engine. My apache is run by root and all the folders are accessable by root.

Please let me know what is the solution for it.

Regards,

Swaroop Kunduru.

---

### Post by jmazzarelli on 2007-07-09
> **SwaroopKunduru said:**
> Hi every one,

Fatal error: [COLOR=Red]Smarty error: unable to write to $compile_dir '/var/www/smarty/templates_c'. Be sure $compile_dir is writable by the web server user. in /usr/local/lib/php/Smarty/Smarty.class.php on line 1095[/COLOR]

I am getting above error. I am running a php file with template engine. My apache is run by root and all the folders are accessable by root.

Please let me know what is the solution for it.

Regards,

Swaroop Kunduru.

Are you sure apache is running as root? Even though you start it as root, it doesn't run as root by default.
```
ps aux | grep apache
```Mine runs as  [FONT="Courier New"]www-data[/FONT]

There is also the chance that the script doesn't create the parent directories before trying to write to a file. Make sure [FONT="Courier New"]/var/www/smarty/[/FONT] exists.

---


---
title: "PHP Freetype"
date: 2008-01-14
forum: Programming Talk
---

### Post by dave333 on 2008-01-14
I'm trying to load a TTF font file in a PHP script using imageloadfont() but it always produces this warning:


Warning: imageloadfont() [function.imageloadfont]: Error reading font in /www/wing/test.php on line 7

I've checked phpinfo() to see if freetype was loaded, but I can't see any reference to it other than in the GD section. How do you install it for Apache2/PHP5 on Gutsy?

Here's what's in some of my phpinfo() output:

Configuration File (php.ini) Path 	
/etc/php5/apache2

Loaded Configuration File 	
/etc/php5/apache2/php.ini

Scan this dir for additional .ini files 	
/etc/php5/apache2/conf.d

additional .ini files parsed 	
/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini, /etc/php5/apache2/conf.d/ps.ini

---

gd
GD Support 	
enabled

GD Version 	
2.0 or higher

FreeType Support 	
enabled

FreeType Linkage 	
with freetype

FreeType Version 	
2.3.5

T1Lib Support 	
enabled

GIF Read Support 	
enabled

GIF Create Support 	
enabled

JPG Support 	
enabled

PNG Support 	
enabled

WBMP Support 	
enabled

---


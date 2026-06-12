---
title: "PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0"
date: 2013-06-09
forum: Programming Talk
---

### Post by jairoh_ on 2013-06-09
how to fix this error in the terminal?
```
PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0

```
tnx

---

### Post by jairoh_ on 2013-06-12
up for this one. anyone can help. tnx

---

### Post by spjackson on 2013-06-12
If you could provide more information, I think that you will be more likely to get help. At the very least, what do you do for that message to occur? If it's code you have written, post the code. Perhaps tell us something about your environment - operating system version, php version etc.

---

### Post by jairoh_ on 2013-06-19
> **spjackson said:**
> If you could provide more information, I think that you will be more likely to get help. At the very least, what do you do for that message to occur? If it's code you have written, post the code. Perhaps tell us something about your environment - operating system version, php version etc.

even typing php-v to know my php version. still shows error. 
```

PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
PHP 5.4.15-1~dotdeb.2 (cli) (built: May 11 2013 20:26:49) 
Copyright (c) 1997-2013 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2013 Zend Technologies
jairoh@jairoh-300E4C-300E5C-300E7C:~/lamp/public_html/l4$ 



```

---

### Post by matt_symes on 2013-06-19
Hi

Page created date is in 2007 but i was last modified in 2011.

[http://www.somacon.com/p520.php](http://www.somacon.com/p520.php)

See if it gets you nearer to a fix.

In future, you may want to add a lot more information to your first post.

You're far, far more likely to get an answer if you give as much detail as possible.

Kind regards

---

### Post by jairoh_ on 2013-06-19
thanks sir but it does not solve. yes that error occurs when i try to see my php version in cli.

---

### Post by SeijiSensei on 2013-06-20
Are you sure this is the version of PHP from the repositories and not one compiled from source?


Take a look in /etc/php5 and see if anything there loads the mcrypt module.

---

### Post by jairoh_ on 2013-07-13
> **SeijiSensei said:**
> Are you sure this is the version of PHP from the repositories and not one compiled from source?


Take a look in /etc/php5 and see if anything there loads the mcrypt module.

when i ran ```
/etc/php5/conf.d$ ls
```
these appeared
 
10-pdo.ini   20-gd.ini      20-mysqli.ini  20-pdo_mysql.ini
20-curl.ini  **20-mcrypt.ini**  20-mysql.ini   [B]mcrypt.ini


[/B]are these what you mean sir?

---

### Post by SeijiSensei on 2013-07-13
Yes, it looks like you have two files that both try to install mcrypt.  The official repository files all start with a number that controls the order of loading.  Rename the file called "mcrypt.ini" to "mcrypt.extra" then restart Apache or run php5 from the command line and see if you still get the error.  If not, and phpinfo() or "php -i" from the command line show mcrypt is still installed, then delete the "extra" file.

---


---
title: "PHP tutorials"
date: 2016-07-04
forum: Programming Talk
---

### Post by dannyk2 on 2016-07-04
Hi, i have just installed PHP but i've can't seem to find any basic PHP tutorials for Linux? Can anyone help me please. Thanks

---

### Post by &amp;KyT$0P# on 2016-07-04
This one helped me: [http://php.net/manual/en/tutorial.php]("http://php.net/manual/en/tutorial.php")

---

### Post by dannyk2 on 2016-07-04
Thanks for the reply and link halogen2

---

### Post by pqwoerituytrueiwoq on 2016-07-04
since you are learning you should change a setting in php's configs

change the [FONT=courier new]display_errors[/FONT] setting to on
it is in this file, though in 16.04 it may be php or php7.0 not php5
[FONT=courier new]/etc/php5/apache2/php.ini[/FONT]
if you don't do that you will get a blank page over anything anything in your web browser and the only way to find out is to read the apache error log file

---

### Post by T.J. on 2016-07-04
This is not a criticism of PHP as much as a warning to save your sanity.  

Please just be aware that PHP has many design issues that have existed for YEARS.  You must load the modules in the proper order for elements of the language to work.  Also, there is no such thing as thread safety under PHP.  Apache and other servers have to use much slower, non-threaded processes  when using PHP or PHP will crash. Last time I checked, the Zend compiler was still a commercial product, so all PHP done without it has to be reloaded and reprocessed each time it is used.  

If want performance on the server side, I urge you to use something else: Perl, C, Java, C#, or even Python would be a better choice than PHP. If you do decide PHP is the way to go, just be prepared for potential bottlenecks should you attempt to scale your code up to a significant number of users.

---


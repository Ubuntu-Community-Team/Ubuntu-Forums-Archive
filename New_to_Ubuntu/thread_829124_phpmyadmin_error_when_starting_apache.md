---
title: "phpmyadmin error when starting apache"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by php-zbatev on 2008-06-14
hi,

I am currently following [this thread]("http://ubuntuforums.org/showthread.php?t=809934&highlight=install+apache"), everything seems to work well except for this error:

root@uBunTabZ:/# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                            [Sat Jun 14 20:17:35 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.

line 3 of apache.conf is: Alias /phpmyadmin /usr/share/phpmyadmin

What does this imply and how should it be fixed.

---

### Post by RealPSL on 2008-06-14
It is hard to tell from the information provided but have you take a look to make sure that you do not already have another alias defined for /phpmyadmin?

---

### Post by Dr Small on 2008-06-14
Apparently there is already another alias defining PhpMyAdmin, creating a loop, causing an error. Simple cause and effect scenario.

---

### Post by b4sakenxx on 2008-07-18
This thread is from a month ago, but I also got this error and want to post my findings in case it helps someone else.

If you get this error:

> root@uBunTabZ:/# sudo /etc/init.d/apache2 restart
* Restarting web server apache2 [Sat Jun 14 20:17:35 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias

I've found that the contents of apache.conf are already being loaded by phpmyadmin.conf located in /etc/apache2/conf.d which means that you can remove the following line from your apache2.conf file.

> INCLUDE /etc/phpmyadmin/apache.conf

Hope this helps!

---

### Post by matiz on 2008-08-27
Okay, 
I have got the same error on my ubuntu 8.04 desktop Lamp box,
any through the tip above, the error was gone, thanks

:lolflag:

---

### Post by matiz on 2008-08-28
New problem occurred&#65292; after I disabled the INCLUDE /etc/phpmyadmin/apache.conf,
I found that I can't open [http://localhost/myphpadmin](http://localhost/myphpadmin)
:mad::(

---

### Post by phattymatty on 2008-09-27
> **b4sakenxx said:**
> This thread is from a month ago, but I also got this error and want to post my findings in case it helps someone else.

If you get this error:



I've found that the contents of apache.conf are already being loaded by phpmyadmin.conf located in /etc/apache2/conf.d which means that you can remove the following line from your apache2.conf file.



Hope this helps!

You are a genius!  Problem solved... I was trying to figure out where that loop was throwing that error.  Good call, problem solved. (although it wasn't causing any errors or conflicts, just that super annoying warning message at stop and start apache.)

---

### Post by wu-man on 2008-09-28
> **b4sakenxx said:**
> 
I've found that the contents of apache.conf are already being loaded by phpmyadmin.conf located in /etc/apache2/conf.d which means that you can remove the following line from your apache2.conf file.


My solution seems to work better because I couldn't find the line you mentioned.

I unlinked the symbolic link to phpmyadmin.conf under /etc/apache2/conf.d/

```
/etc/apache2/conf.d$ unlink phpmyadmin
```

---

### Post by lee.eden on 2009-02-27
Got it!  The trick is this: don't change anything in any of the files, but this is how to find phpMyAdmin in ubuntu, use **[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)** (all lower case) and it works.  This is because the  **/etc/apache2/conf.d/phpmyadmin.conf** file includes the command **Alias /phpmyadmin /usr/share/phpmyadmin** which explains why **[http://localhost/phpMyAdmin/](http://localhost/phpMyAdmin/) **doesn't work any more... (camel case)

---

### Post by rjgoldsborough on 2010-07-08
I see this post is old, but I just wanted to say I was getting the same error on Ubuntu 10.04 and removing 'INCLUDE /etc/phpmyadmin/apache.conf' fixed the problem

---


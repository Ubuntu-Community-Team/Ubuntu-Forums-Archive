---
title: "Need Help setting up an error log for PHP errors"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by eldan2 on 2013-08-06
Hey,

I was going through a tutorial that shows how to specify an error log. On the tutorial they set the error_log = /media/sf_sandbox/php_errors.log 
on the /etc/php5/apache2/php.ini
My question is how did the set up the file, because it didn't show that on the tutorials.

When i ran the command tail "-f /media/sf_sandbox/php_errors.log" it gave me the following warning ...cannot open `/media/sf_sandbox/php_errors.log' for reading: No such file or directory


Any help would be highly appreciated! Thanks

---

### Post by HeroOfCanton on 2013-08-07
Apache logs by default at 
```
/var/log/apache2/error.log
```

Is there a reason you needed a different location? If not, you can just delete the line you added in php.ini and check the log there. Otherwise:

AFAIK, you do not need to do anything special to set the log up, although you probably want to make sure the directory you're pointing to actually exists on your system rather than just using a random tutorial location.

---

### Post by eldan2 on 2013-08-07
Thanks for that info! It worked. 

The reason why I wanted it in  another folder is because I heard its better practice to store the logs  in a place other then apache is that true?

---

### Post by eldan2 on 2013-08-07
Also how can I clear all the log file and start clean?

---

### Post by slickymaster on 2013-08-07
> **eldan2 said:**
> Also how can I clear all the log file and start clean?

I would suggest to rename the log, and create a new one. First, rename the current log file:```
mv /var/log/apache2/error.log /var/log/apache2/error.log.1
```Second, create a new log file and give the same permissions, owner/group and selinux context, as the original one:```
sudo touch /var/log/apache2/error.log
sudo chown --reference=/var/log/apache2/error.log.1 /var/log/apache2/error.log
sudo chmod --reference=/var/log/apache2/error.log.1 /var/log/apache2/error.log
sudo restorecon --reference=/var/log/apache2/error.log.1 /var/log/apache2/error.log
```Next, restart apache

---

### Post by pqwoerituytrueiwoq on 2013-08-07
If you look in your sites configuration file located in [FONT=courier new]/etc/apache2/sites-available/[/FONT] you can define a alternate error log file
the files there work like a [FONT=courier new].htaccess[/FONT] file
this should be helpful
[http://perishablepress.com/how-to-enable-php-error-logging-via-htaccess/](http://perishablepress.com/how-to-enable-php-error-logging-via-htaccess/)

---

### Post by eldan2 on 2013-08-07
Okay gotchya! Thanks slickymaster

---

### Post by eldan2 on 2013-08-07
got it! Thanks!

---

### Post by SeijiSensei on 2013-08-08
> **eldan2 said:**
> The reason why I wanted it in  another folder is because I heard its better practice to store the logs  in a place other then apache is that true?

I've used PHP for well over a decade, and I have never heard of that "better practice."  I do set up separate access and error logs for each virtual host, but a separate file for PHP errors?  Not really worth it in my mind.  I guess I could see this being useful if you have a bunch of developers who need to see the errors but don't need root permissions.  For an individual or small shop, it seems like overkill.

You might also want to look into **logrotate** which will automatically rotate logs every day, week, or month. See "man logrotate" for details.

---


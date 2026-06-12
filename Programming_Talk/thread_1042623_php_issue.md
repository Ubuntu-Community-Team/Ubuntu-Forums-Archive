---
title: "php issue"
date: 2009-01-17
forum: Programming Talk
---

### Post by shahin on 2009-01-17
Greetings-
   I am trying to implement this procedure: [http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10](http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10) , and having some issue with php.  When I try to view any page in my web directory, firefox asks what application to use to open the file, and if I want to save it.  This started when I tried to fix another php error I was receiving.  Now I can not even view the phpinfo() results.

---

### Post by utnubuuser on 2009-01-17
I suppose you've tried restarting the server?

---

### Post by shahin on 2009-01-17
Yes I restarted apache2

---

### Post by shahin on 2009-01-17
No I still get the same behavior.  Restarting did not help.

---

### Post by sunset_studies on 2009-01-18
could be many things...

have you tried this?

sudo a2enmod php5

---

### Post by shahin on 2009-01-18
I did that.  It is still doing the same thing.  I have to say I am running Firfox 3.0(5).  I saw somethings about Mozilla doing this, but I could really find th fix.

---

### Post by DocForbin on 2009-01-18
It has nothing to do with your web browser. Apache is not running php for whatever reason. What changes did you make to your apache configuration? Have you looked at your logs? If nothing else reinstall php...

---

### Post by shahin on 2009-01-18
Here is the logs from the error file:
[Sun Jan 18 07:36:51 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sun Jan 18 10:21:21 2009] [notice] Graceful restart requested, doing restart
[Sun Jan 18 10:21:21 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
Here is the logs from the access log:
[Sun Jan 18 07:36:51 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sun Jan 18 10:21:21 2009] [notice] Graceful restart requested, doing restart
[Sun Jan 18 10:21:21 2009] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations

Is there any other logs I can look at before re-installing?

---

### Post by shahin on 2009-01-18
Here is the access log output:
192.168.1.2 - - [18/Jan/2009:10:21:33 -0500] "GET /test.php HTTP/1.1" 304 - "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008
041514 Firefox/3.0b5"
192.168.1.2 - - [18/Jan/2009:10:22:34 -0500] "GET /web/base-php4/setup HTTP/1.1" 301 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b
5) Gecko/2008041514 Firefox/3.0b5"

I mistakenly pasted the error log twice in the previous reply.

---

### Post by Reiger on 2009-01-18
This sounds like a case for the old-tried-and-true: reinstall the whole lot. Granted, it's a lot like how you fix Windows trouble but unless you are very experienced (and I gather you're not because you did not dismiss the restart option) it is probably by far the easiest thing to do anyways.
At the core:
So to try and be of actual help (the -y switch will skip all confirmation prompts and assume a yes vote on all count; since the fault may very well be at the configuration files, use purge instead of remove and use a separate install command):
```

sudo aptitude -y purge [Fill in all apache2 and php modules you have, mind: if you use php 5 then all php5 modules will be called something-php5 or php5-something]
sudo aptitude -y install [Fill in the same thing, again]

```

Because this is tedious I suggest you do the following first:
```

aptitude search apache2 php | grep -E '^i' > list_of_packages

```

Then edit the file to contain only the package names themselves, one on each line. This will make automation a bit easier:
'Refined':
```

cat list_of_packages | perl -e 'while(<>) { system("sudo aptitude -y purge ".$_); }'
cat list_of_packages | perl -e 'while(<>) { system("sudo aptitude -y install ".$_); }'

```

---

### Post by Namtabmai on 2009-01-18
Sounds like apache2 isn't enabling php5 on your system. Check the following directory

/etc/apache2/mods-enabled/

And see if you have the files
php5.load
php5.conf

The php5.load should have a line like

LoadModule /usr/lib/apache2/modules/libphp5.so

---

### Post by drubin on 2009-01-18
> **shahin said:**
> Greetings-
   I am trying to implement this procedure: [http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10](http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10) , and having some issue with php.  When I try to view any page in my web directory, firefox asks what application to use to open the file, and if I want to save it.  This started when I tried to fix another php error I was receiving.  Now I can not even view the phpinfo() results.

Take a look at the link in my sig for installing php/apache. I think it is much better howto then the outdated one on whotoforge.

Also it does seem like you need libapache2-mod-php5

---

### Post by shahin on 2009-01-18
I checked the apache2 modules, and the line is there.  Here is what is in the php5.load file:
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

I appreciate the new link.  I think I will have a look.  I have followed the howtoforge recipe twice now.  I think my issue is version compatibility for the different softwares.  The procedures sometimes call for the latest version of the software, but different versions put things in different files, and/or have different dependencies.

---

### Post by shahin on 2009-01-19
I think I found the issue.  I just reboot the machine, and I see this error message in the apache2 logs:
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mysql.so' - /usr/lib/php5/ext/mysql.so: undefined symbol: PL_mem
ory_wrap in Unknown on line 0
PHP Warning:  Module 'gd' already loaded in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mysqli.so' - /usr/lib/php5/ext/mysqli.so: cannot open shared obj
ect file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/pdo.so' - /usr/lib/php5/ext/pdo.so: cannot open shared object fi
le: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/pdo_mysql.so' - /usr/lib/php5/ext/pdo_mysql.so: cannot open shar
ed object file: No such file or directory in Unknown on line 0
[Mon Jan 19 17:02:51 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5 with Suhosin-Patch configured -- resuming normal operations

When I look int the /usr/lib/php5/ext directory I see two files, gd.so and mysql.so, I am not sure why apache2 is not able to find the file or how to fix this.  I also do not know what are the other files like, pdo_mysql.so, and pdo.so.  I do not have them in my php5/ext directory.

---

### Post by drubin on 2009-01-19
> **drubin said:**
> Take a look at the link in my sig for installing php/apache. I think it is much better howto then the outdated one on whotoforge.

Also it does seem like you need libapache2-mod-php5

> **shahin said:**
> 
When I look int the /usr/lib/php5/ext directory I see two files, gd.so and mysql.so, I am not sure why apache2 is not able to find the file or how to fix this.  I also do not know what are the other files like, pdo_mysql.so, and pdo.so.  I do not have them in my php5/ext directory.

Did you install **libapache2-mod-php5** like I said ealier?

The default install of php/apache/mysql goes off with out a hitch. What have you changed/not installed since then.

I suggest re-tracing your steps. This is very important to know what has been changed/re-configured on your system. If you have made any changes that could result in in-securities it is NB to know what they are. (Or start from scratch again)

---

### Post by shahin on 2009-01-19
Ok that issue seems to be out of the way.  The instructions in [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205) stated to reinstall libapache2-mod-php5, and as soon as I tested it, it is working now.  Thanks.  
Now I am getting another error:
Fatal error: Call to undefined function mysql_connect() in /var/www/adodb5/drivers/adodb-mysql.inc.php on line 363
Which almost everyone says it has to do with the php extensions.  But the files are there.  What should I do?  Should I reinstall them also?  I already checked the php.conf file, and the lines for mysql.so, and gd.so are uncommented, and the directory path seems to be correct also.

---

### Post by drubin on 2009-01-19
> **shahin said:**
> Ok that issue seems to be out of the way.  The instructions in [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205) stated to reinstall libapache2-mod-php5, and as soon as I tested it, it is working now.  Thanks.  
Now I am getting another error:
Fatal error: Call to undefined function mysql_connect() in /var/www/adodb5/drivers/adodb-mysql.inc.php on line 363
Which almost everyone says it has to do with the php extensions.  But the files are there.  What should I do?  Should I reinstall them also?  I already checked the php.conf file, and the lines for mysql.so, and gd.so are uncommented, and the directory path seems to be correct also.

Follow the rest of the tutorial explaining how to install the php - mysql modules.

something like php5-mysql

---

### Post by shahin on 2009-01-20
I installed apache2 just like it was in the tutorial. Then I removed all php installs from my machine I could find.  It was interesting that when I create a php file, and load it in my browser, I can view it.  The file just contains the phpinfo() function.  I did a search in synaptic for php, and here is all the files on my machine that has the word php in them.  If you can identify which one is actually processing the php code, I would sure appreciate it:
hplip, libapache2-mod-php5, libgtksourceview2.0-common, libgtksourceview-common, notification-daemon, php5-common, totem-xine, xine-ui.


Can you review the howtoforge procedure and let me know if I need different php compounents stated in there please?  the procedure calls for php5.gd, and a few others which the tutorial does not mention.  I am not sure if those components are for php4 only, or I am going to need them when I want to user acid, base, and snort with everything else.  So far the tutorial is great. Thank you for spending time on it.

---

### Post by shahin on 2009-01-20
The procedures state to go to
/home/user/public_html/base-php4/setup
Find the line that says "base_header" and change it to "header".
But I do not find it.  Could this have been changed in the new release?
Also I am not sure if the latest base version is compatible with php5.  I saw a document online that php5 is backwards compatible.  But after the issues I run into, I want to be more cautious.

---

### Post by shahin on 2009-01-20
The other issue I am running into is that pear can not find the dynamic libraries even I after I move them to the location it is expecting to see them.  What can I do please?

Here is the first message 
root@thunder:/home/sansari/public_html/base-php4/setup# pear install Image_Color
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  Module 'mysql' already loaded in Unknown on line 0
Ignoring installed package pear/Image_Color
Nothing to install

Then I did 

root@thunder:/usr/lib/php5/ext# cp * /usr/lib/php5/20060613+lfs/
root@thunder:/usr/lib/php5/ext# ls
gd.so  mysql.so
root@thunder:/usr/lib/php5/ext# cd /usr/lib/php5/20060613+lfs/
root@thunder:/usr/lib/php5/20060613+lfs# ls
gd.so  mysqli.so  mysql.so  pdo_mysql.so  pdo.so
root@thunder:/usr/lib/php5/20060613+lfs# 


But when I ran pear again, I see the same error 

root@thunder:/home/sansari/public_html/base-php4/setup# pear install Image_Color
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysql.so' - /usr/lib/php5/20060613+lfs/mysql.so: undefined symbol: PL_memory_wrap in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysql.so' - /usr/lib/php5/20060613+lfs/mysql.so: undefined symbol: PL_memory_wrap in Unknown on line 0
Ignoring installed package pear/Image_Color
Nothing to install

---

### Post by shahin on 2009-01-20
Ok seems I am running into a bug, and I do not see any fix for it. Here is the link I found
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/120103](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/120103)
There is a lot of postings about php5 issues with different dynamic libraries.

---


---
title: "[SOLVED] Testing Local PHP files Using LAMP Server"
date: 2008-07-04
forum: Programming Talk
---

### Post by brennydoogles on 2008-07-04
Hello, I am trying to figure out how to do this, but I am failing miserably. If anyone has any input it would be great. Thanks!!

---

### Post by henchman on 2008-07-04
I don't know at which stage you are, but i just installed apache2, php5, php5-mysql (or something like that), mysql-server, mysql-client and then, everything is up and running(?) :-)

you may need to start the server by invoking ```
sudo /etc/init.d/apache2 start
``` and ```
sudo /etc/init.d/mysql start
```

then you can put your stuff into /var/www as this is the default documentroot...

you may also sudo apt-get install phpmyadmin :)

---

### Post by soapytheclown on 2008-07-04
are the php files in the apache folder (by default /var/www)?
are you accessing them through the browser ie: [http://localhost/test.php](http://localhost/test.php)

sorry if theyre obvious but u didnt provide much info

-edit henchamn got there b4 me :) -

---

### Post by brennydoogles on 2008-07-05
I actually followed [this tutorial from Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_for_local_web_development") to set it up, but whenever I try to access the PHP file I get an error. Any Ideas?

---

### Post by LaRoza on 2008-07-05
> **brennydoogles said:**
> I actually followed [this tutorial from Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_for_local_web_development") to set it up, but whenever I try to access the PHP file I get an error. Any Ideas?

What is the error?

---

### Post by brennydoogles on 2008-07-05
> **LaRoza said:**
> What is the error?

Here is a screenshot of the error.

---

### Post by Can+~ on 2008-07-05
Did you add read permissions to "others"?

```
sudo chmod -R o+r THE_WWW_FOLDER
```

Also, the guide didn't mention the libapache2-mod-php5?

---

### Post by brennydoogles on 2008-07-05
> **Can+~ said:**
> Did you add read permissions to "others"?

```
sudo chmod -R o+r THE_WWW_FOLDER
```

Also, the guide didn't mention the libapache2-mod-php5?

Now would I need to do this to the /var/www/ folder, or the ~/www/ folder created in the next part of the guide?

---

### Post by henchman on 2008-07-05
Try this on ~/www/, because that's the directory, where the server has to read the files :)

---

### Post by brennydoogles on 2008-07-05
It seems we are getting somewhere, but still not where we need to be. I can now access files in /var/www/ through the browser, but instead of parsing them it gives me the option to download them. Here is a screenshot....

---

### Post by cpetercarter on 2008-07-05
Hav a look at [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

> Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php4.[ED: I think this should be -php5 if you have php5 installed] It is installed when you install the php4 package, but may have been removed inadvertently by packages which need to run a different version of php.

You may also need to actually enable it, by doing sudo a2enmod php4 [ED; ?php5]followed by sudo /etc/init.d/apache2 restart. If sudo a2enmod php4 [?5]returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it.

Be sure to clear your browser's cache before testing your site again. 

---

### Post by Can+~ on 2008-07-05
> **brennydoogles said:**
> It seems we are getting somewhere, but still not where we need to be. I can now access files in /var/www/ through the browser, but instead of parsing them it gives me the option to download them. Here is a screenshot....

Ok, your apache server doesn't know what to do with php.

```
sudo apt-get install libapache2-mod-php5
```

Restart apache2, and test it again.

---

### Post by brennydoogles on 2008-07-05
Ok, using the help.ubuntu.com link really helped, now I can view most of my pages. Somethings are not working correctly, such as an AJAX news script I wrote (which works fine on my godaddy.com hosting), but I can work on that more later. Thanks for all of the help!!

---

### Post by pmasiar on 2008-07-05
I am curious why you picked such combination of tools, as a beginner? If starting with Python/Turbogears, and installing all by docs, you can have running webserver with database in less than hour. Of course, it will not be production-ready Apache, but developer's friendly CherryPy. Your database will not be MySQL but  much simpler SQLite. But your "hello world" app will be generated for you, including install, in less than hour (including proper directory structure for future project, including JS and CSS files), and you can later change to MySQL - you just change config file. Same with Apache - but as beginner, you might be more interested in devel-friendly tools, not LAMP, which is  optimized as effective production webserver.

Just a thought about your priorities - you know better what they are.

---

### Post by brennydoogles on 2008-07-05
> **pmasiar said:**
> I am curious why you picked such combination of tools, as a beginner? If starting with Python/Turbogears, and installing all by docs, you can have running webserver with database in less than hour. Of course, it will not be production-ready Apache, but developer's friendly CherryPy. Your database will not be MySQL but  much simpler SQLite. But your "hello world" app will be generated for you, including install, in less than hour (including proper directory structure for future project, including JS and CSS files), and you can later change to MySQL - you just change config file. Same with Apache - but as beginner, you might be more interested in devel-friendly tools, not LAMP, which is  optimized as effective production webserver.

Just a thought about your priorities - you know better what they are.

LOL... I understand what you mean. My idea to install a LAMP server was not thought out in advance at all... in fact, there was a php file that I did not want available on the web until it was finished, and I wanted to be able to test it without uploading it to my main server. It seems that I now have everything configured more or less properly (the problem with the AJAX was just a configuration issue caused by the change from my normal domain name to localhost). So while it was somewhat haphazardly that I decided upon LAMP, I now have it set up more or less to my liking and will keep it for now.

---


---
title: "How to setup Apache + MySql + PHP + phpMyAdmin + WordPress"
date: 2007-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by tarek on 2007-05-27
This is a step by step tutorial to setup your server and blog.

[URL="http://blog.csmonkey.com/2007/05/how-to-setup-apache-mysql-php.html"]http://blog.csmonkey.com/2007/05/how-to-setup-apache-mysql-php.html
[/URL]

Your feedback and questions are welcome.

UPDATED.

---

### Post by goodtimetribe on 2007-06-02
Very nice tutorial! It worked on the first try, even though MySQL was already installed. I'm using edgy, btw.

thanks for the tutorial!

---

### Post by Cool Surfer on 2007-06-04
Excellent!!

---

### Post by hairyhi on 2007-06-26
> **tarek said:**
> This is a step by step tutorial to setup your server and blog.

[http://csmonkey.com/blog/2007/05/24/how-to-setup-apache-mysql-php-phpmyadmin-wordpress/](http://csmonkey.com/blog/2007/05/24/how-to-setup-apache-mysql-php-phpmyadmin-wordpress/)

Your feedback and questions are welcome.

I guess doesn't exist any longer

---

### Post by b00gie on 2007-06-26
Indeed. Link seems to be broken :(

---

### Post by az on 2007-06-26
Here is the Wordpress howto from help.ubuntu.com:

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by tarek on 2007-06-26
> **az said:**
> Here is the Wordpress howto from help.ubuntu.com:

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

Sorry, forgot to update the url. Try it now.

---

### Post by az on 2007-06-26
> **tarek said:**
> Sorry, forgot to update the url. Try it now.

$ sudo chown –R www-data blog
$ sudo chgrp –R www-data blog
$ sudo mv blog/ /var/www/


That's not secure!


As well,  are you using the database as the mysql-root user?

---

### Post by tarek on 2007-06-26
Hi az,

$ sudo chown &#8211;R www-data blog
$ sudo chgrp &#8211;R www-data blog
$ sudo mv blog/ /var/www/

The above is good because by default the files are owned by root, which means you cannot edit wordpress from the admin screen.

In the tutorial I did not suggest/recommend using the root user in mysql, but I recommend setting a password since by default the root user dones't have a password for mysql.

TK

---

### Post by az on 2007-06-26
> **tarek said:**
> Hi az,

$ sudo chown –R www-data blog
$ sudo chgrp –R www-data blog
$ sudo mv blog/ /var/www/

The above is good because by default the files are owned by root, which means you cannot edit wordpress from the admin screen.


You should not need to make the whole directory writeable.  If anything, you should make the configuration file writeable during the configuration and then change it back to read-only.  You can compromise your whole database (not to mention filesystem if you allow the web server to write to the directory) that way.

You should make writeable as little as possible.

> **tarek said:**
> 
In the tutorial I did not suggest/recommend using the root user in mysql, but I recommend setting a password since by default the root user dones't have a password for mysql.

TK

You do not describe how to create a mysql user with limited permissions and prviledges.  The deb package does this for you.

---

### Post by tarek on 2007-06-26
Oh boy ... I'm talking about customizing plugins, themes and other files that can be modified from the administration screen in wordpress. My tutorial works and it's secure.

TK

---

### Post by az on 2007-06-26
> **tarek said:**
> Oh boy ... I'm talking about customizing plugins, themes and other files that can be modified from the administration screen in wordpress. My tutorial works and it's secure.

TK

[http://codex.wordpress.org/Changing_File_Permissions](http://codex.wordpress.org/Changing_File_Permissions)

"All files should be owned by your user account, and should be writable by you. Any file that needs write access from WordPress should be group-owned by the user account used by the webserver."

In this context, you = your user and webserver = www-data.


You ideally don't wnat anything to be writeable by www-data in your web application.  For example, if there was some vulnerability in your WYSIWYG editor, someone could upload a script and get php to run it.  Most web applications have an uploads directory where you need to allow the webserver to write, though.  The less that is writable, the better.

---

### Post by speaker219 on 2007-06-26
Easy instructions on how to install something like this:
[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

---


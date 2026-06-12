---
title: "LAMP local server installation on Ubuntu 8.04 Hardy Heron."
date: 2008-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by sanus|art on 2008-05-27
**[1]** - Installation:

This will install 'Apache 2', 'php5', 'MySQL' and 'phpMyAdmin' (if you need php4 rather than php5 - just change 5's to 4's in the code bellow):

```

sudo apt-get install apache2 php5 libapache2-mod-php5 mysql-server libapache2-mod-auth-mysql php5-mysql phpmyadmin

```_NOTE !_ You'll be asked to provide SQL password durring the MySQL installation.

**[2]** - Configure:
Add 'phpMyAdmin' module to apache:
```

echo "Include /etc/phpmyadmin/apache.conf" | sudo tee -a /etc/apache2/apache2.conf

```_NOTE !_ If you get 'blowfish password error' in [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) see the second post by [**antiigrav**]("http://ubuntuforums.org/showpost.php?p=5160992&postcount=2") in this tread.
_NOTE !_ the default username is 'root', the default password is whatever you specified at the stage [1] at the MySQL installation. 

Edit the file */etc/apache2/httpd.conf* (it might be empty - don't worry):
```


sudo gedit /etc/apache2/httpd.conf

```and add this (my username and user group is called 'sasha' - change it to yours):
```

ServerName localhost
User sasha
Group sasha

```This will grant you access as the specified user.

**[3]** - Testing the installation:
Restart the apache for new setting to be applied:
```

sudo /etc/init.d/apache2 restart

```To test Apache2 installation - point your web browser to:
```

http://localhost/

```You should see page which reads 'It works!'.
To test php installation - create file called *test.php* in */var/www* or type in terminal:
```

echo '<?php phpinfo(); ?>' | sudo tee /var/www/test.php

```and point your web browser to:
```

http://localhost/test.php

```You should see page which tells different php settings like in the picture:
[ATTACH]71843[/ATTACH]
To test phpMyAdmin installation point your web browser to:
```

http://localhost/phpmyadmin

```**[4]** - Re-configurations (optional):
By default, apache2 is set to listen to port *80* at *[http://localhost/](http://localhost/)* while the server's root directory is */var/www*.
(a) - to change the port - edit the file */etc/apache2/ports.conf* and change the 'Listen 80' to some other number:
```

sudo gedit /etc/apache2/ports.conf

```(for example: if you change 80 to 4747 - you can access the server root by *[http://localhost:4747/](http://localhost:4747/)*)

(b) - to change the 'server root' - edit the file */etc/apache2/sites-available/default*:
back-up the original file:
```

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/default_backup

```... and open the file for editing:
```

sudo gedit /etc/apache2/sites-available/default

```change the content to something like the following:
(this is my settings - I wanted my server to be accessed from 'http://www' while all my web files are located at '/home/sasha/www')
```

NameVirtualHost *
<VirtualHost *>
    ServerName www
    DocumentRoot /home/sasha/www
</VirtualHost>

```now go to SYSTEM => ADMINISTRATION => NETWORK at the HOST tab select localhost, and add 'www' as it shows in the picture:
[ATTACH]71844[/ATTACH]
Or edit file /etc/hosts
```
sudo gedit /etc/hosts
```
Now restart the apache:
```

sudo /etc/init.d/apache2 restart

```Now test it by pointing your web browser to:
```

http://www

```(c) - To add more virtual hosts - just repeat the (b) part with the ServerName and DocumentRoot specification, add the ServerName to SYSTEM => ADMINISTRATION => NETWORK the HOST tab, restart apache.


Hope I didn't forgot/messed things up or worse, if I did - please feel free to correct me.

---

### Post by antiigrav on 2008-06-11
works well thanks.

as mentioned above, to fix initial blowfish error on phpmyadmin startup page:

from **/var/lib/phpmyadmin/blowfish_secret.inc.php**
copy the line like **$cfg['blowfish_secret'] = 'your hash here';**
and paste it at the end of **/etc/phpmyadmin/config.inc.php**

---

### Post by sanus|art on 2008-06-11
Thanks antiigrav,
Didn't noticed the error (did not worked with SQL for about a 6 months), I'll edit the tutorial.

---

### Post by JT9161 on 2008-06-14
Thanks for the Tutorial everything works great. But do you how I would set up a part of my site to be password protected ? I know I need a combo of a .htaccess file in /var/www and a .htpasswd file in my private folder but I have no idea how to go about this.

---

### Post by sanus|art on 2008-06-14
> **JT9161 said:**
> Thanks for the Tutorial everything works great. But do you how I would set up a part of my site to be password protected ? I know I need a combo of a .htaccess file in /var/www and a .htpasswd file in my private folder but I have no idea how to go about this.
Basically you need to specify full server path to .htpasswd file in .htaccess, create username/s and encripted password/s and specify protected directory.

Here is some tutorial:
[http://www.elated.com/articles/password-protecting-your-pages-with-htaccess/](http://www.elated.com/articles/password-protecting-your-pages-with-htaccess/)

Here are password encription generator:
[http://www.kxs.net/support/htaccess_pw.html](http://www.kxs.net/support/htaccess_pw.html)

---

### Post by tananaBrian on 2008-10-04
> **antiigrav said:**
> works well thanks.

as mentioned above, to fix initial blowfish error on phpmyadmin startup page:

from **/var/lib/phpmyadmin/blowfish_secret.inc.php**
copy the line like **$cfg['blowfish_secret'] = 'your hash here';**
and paste it at the end of **/etc/phpmyadmin/config.inc.php**

Yes!  Thank you!  It would have taken me bazillions of years to figure this one out!

Brian
Fox, Alaska... Got snow?

---

### Post by and.duncan on 2008-11-09
Hi,

Just updating for my experience with 8.10:

In [1] after the MySQL password was entered it asked me which web server to automatically configure phpmyadmin in, I selected apache2 and didn't perform the step in [2] nor the added blowfish bit. Step [3] was followed as written and it all seems to work, took 5 mins :) (I'm expecting something to be horribly wrong somewhere... still looking for it)

---

### Post by skym on 2009-02-17
Thanks for the tutorial..however am still having a problem.
When I finish the step and want to test the [http://localhost](http://localhost) on the browser, it doesnt work.
On the command prompt its giving me this message:
 [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
What can I do to solve this problem...
plz I need help

---

### Post by sanus|art on 2009-02-18
Could you post the content of your /etc/apache2/sites-avaliable/default and /etc/hosts here?

---


---
title: "Changing Apache directory"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Vignesh Sankaran on 2012-07-23
So I'm currently setting up a web server in ubuntu, and I want to change the root directory of the website from /var/www to /home/vignesh/website-www. I followed instructions from [HTML]<a href="http://www.ajopaul.com/2010/05/01/ubuntu-apache2-change-default-documentroot-varwww/">here</a>[/HTML], but I'm not entirely sure if it worked, as it came up with this piece of code that looked like an error

```
 
* Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

It also changed the website look to what is attached, compared to the standard "It works!" webpage that I was seeing prior to this root directory move attempt. 

Am I over-worrying here or is something not quite right?

Oh and here is the edited default document
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/vignesh/website-www/
    <Directory /home/vignesh/website-www/>
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/vignesh/website-www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by mastablasta on 2012-07-23
did you put index.html into that directory (/home/vignesh/website-www)?

---

### Post by TheFu on 2012-07-23
What are the directory permissions on 
* home/vignesh
* home/vignesh/website-www

Don't forget that web servers usually run as www-data user so your HOME permissions might be blocking access. You want "other" to have read-execute and you might want home/vignesh/website-www to be owned by group www-data with rwx permissions - but you definitely need for www-data user or group to be able to read that directory by either group or "other" access permissions.

I think your 
```
<Directory /home/vignesh/website-www/>
```should be 
> <Directory / >to tell it the root directory of your webserver.

---

### Post by Vignesh Sankaran on 2012-07-23
> I think your 
 	Code:
 	<Directory /home/vignesh/website-www/> 
should be 
 	Quote:
 	 	 		 			 				<Directory / > 			 		 	 	 
to tell it the root directory of your webserver. 	

Ah yeah, I remember changing that too, I thought I was supposed to change that as well. 

And no I haven't put my index.html inside yet, I want to see if the default welcome screen will come back first before I give that a shot.

---

### Post by greenpeace on 2012-07-24
> **Vignesh Sankaran said:**
> I want to see if the default welcome screen will come back first before I give that a shot.

Might be best to put a simple index.html file in there so that you know what you're expecting to see... 

The default page is an actual index.html file that apache installs by default into /var/www/ ... so make sure you have something there to be displayed!  :)

---

### Post by Vignesh Sankaran on 2012-07-28
Yep I put my index.html file into the new directory and it works :). Thanks for all the help guys

---


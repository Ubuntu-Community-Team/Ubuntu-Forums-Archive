---
title: "After upgrade to 10.04: php files not interpreted but offered as a download"
date: 2010-05-17
forum: Programming Talk
---

### Post by kd_jm on 2010-05-17
After upgrading to UNR 10.04 I can no longer run php scripts inside a user website. Before the upgrade, this worked (UNR 9.10).

A lamp configuration is setup for local website development, using "UserDir" feature, so my website can be accessed via [http://localhost/~USERNAME](http://localhost/~USERNAME)

Html files are displayed just fine, and also the correct php file can be located. But instead of interpreted, it is merely offered as a download. I added a test php file in the root of the local website (in /var/www, accessible via [http://localhost/](http://localhost/), and that php script is interpreted just fine. 
So it is only the combination that gives a faulty behavior: a php file inside a UserDir is sent to the browser unaltered (as type application/x-httpd-php).

I searched for a solution (google), but no solution offered was helpful. I also deleted (and purged) all of apache, php and mysql I could find, and re-installed an entire fresh lamp setup (using the task feature of apt-get), but the same error persists.

When accessing the php script in a user directory, no error is logged in the apache error log file. Output of the phpinfo() info call is attached. 

What do I do wrong?

---

### Post by Reiger on 2010-05-17
It's because by default Ubuntu is configured *not* to enable PHP5 interpreters in userdir tree. This is presumably good for server deployment because it is of course a security concern if any random user is able to execute arbitrary CGI scripts and the like... but it isn't so helpful in test/development installations.

You'll need to edit Apache configuration /etc/apache2/mods-enabled/php5.conf (here's mine):
```

<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
        SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
        SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    #<IfModule mod_userdir.c>
    #    <Directory /home/*/public_html>
    #        php_admin_value engine Off
    #    </Directory>
    #</IfModule>
</IfModule>

```
Then restart Apache2 and your PHP scripts should run again.

---

### Post by kd_jm on 2010-05-18
Ahh... That was the reason! Thank you, your solution works like a charm. 
I somehow completely missed that when looking through the available doucmentation online. And strange this did work in 9.10, I certainly did not alter that module configuration file.

Thanks a lot!

---


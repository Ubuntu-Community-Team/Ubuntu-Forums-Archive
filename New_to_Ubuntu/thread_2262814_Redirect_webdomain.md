---
title: "Redirect webdomain"
date: 2015-01-27
forum: New to Ubuntu
---

### Post by Ahmed_Ibrahim on 2015-01-27
I am having a web site that is working through [http://www.domain.com/LMS/Course]("http://www.alakademia.com/NITLMS/Courses/")
 
I need it to work directly from [http://www.domain.com](http://www.domain.com)

I did .htaccess contains the following but it is not working:

Redirect [http://www.domain.com/index.htm](http://www.domain.com/index.htm) [http://www.domain.com/LMS/Course](http://www.domain.com/LMS/Course)

Didn't work

Then I changed .htaccess file to contain:

Options +FollowSymlinks
RewriteEngine on
rewritecond %{http_host} ^domain.com [nc]
rewriterule ^(.*)$ http://www.domain.com/LMS/Course/$1 [r=301,nc]

But it is not working too

What is the problem?

---

### Post by Lars Noodén on 2015-01-27
If it's your server, then you can avoid the mess of .htaccess and work directly in the configuration file for that virtual host.  Then the rewrite rules usually go in a <Directory> stanza.  Also, did you turn on [mod_rewrite](http://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)?

```

sudo a2enmod rewrite
sudo service apache2 restart

```

What are the symptoms of it not working and what is / isn't showing up in the error logs?

---

### Post by Ahmed_Ibrahim on 2015-01-27
What I wrote above is exactly what I did
Now I am having .htaccess file in the root containing the following:

[COLOR=#000000]Options +FollowSymlinks[/COLOR]
[COLOR=#000000]RewriteEngine on[/COLOR]
[COLOR=#000000]rewritecond %{http_host} ^alakademia.com [nc][/COLOR]
[COLOR=#000000]rewriterule ^(.*)$ http://www.alakademia.com/NITLMS/Courses/$1 [r=301,nc]

[/COLOR]I don't know if I am writing the .htaccess file content right or wrong but I got that from the web
I am saying that it is not working as when I write [http://www.alakademia.com/](http://www.alakademia.com/) it is not directing to the needed site but still displaying the root file

---

### Post by Lars Noodén on 2015-01-28
Ok.  I would find a guide that avoids use of .htaccess   Since it is your own server you are allowed to make changes to the configuration file and do not need a hack like .htaccess.  It is fine for situations where you are not allowed access to the web server's configuration although the sysadmin is willing to farm out a few configuration options.  

About the configuration itself, your formula works if it goes inside a [Directory](http://httpd.apache.org/docs/2.4/mod/core.html#directory) or [Location](http://httpd.apache.org/docs/2.4/mod/core.html#location) clause in the main configuration for your virtual host.  

```

<VirtualHost *:80>
 ...
  <Directory /var/www/html>
    RewriteEngine on
    RewriteCond %{http_host} ^example.com [nc]
    RewriteRule  ^(.*)$ http://www.example.com/LMS/Course/$1 [r=301,nc]
  </Directory>
</VirtualHost>


```

If you have still the default settings and only one site on your server then this would be the file */etc/apache2/sites-enabled/000-default.conf*

---

### Post by SeijiSensei on 2015-01-28
Can't you just point the DocumentRoot to /var/www/html/LMS/Course or wherever the new root directory is located?
```

<VirtualHost *:80>
    ServerName www.domain.com

    DocumentRoot /var/www/html/LMS/Course
    <Directory "/var/www/html/LMS/Course">
        [stuff]
    </Directory>

    [more stuff]

</VirtualHost>

```

---

### Post by Ahmed_Ibrahim on 2015-01-28
Great;
Thank you all
I did the task by setting two different Apache Virtual Hosts
The following link is really good
[https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)

---


---
title: "Apache/2.4.6 update causes 404s"
date: 2014-01-02
forum: Programming Talk
---

### Post by aaron.lote on 2014-01-02
Hello :)

I'm running a ec2 ubuntu instance, I decided to update my PHP today to 5.5.7, unfortunately it triggered apache to update as well, which has caused me many errors, the biggest one is my rewrite rules are no longer being hit and I believe its something todo with .conf changes.

My site conf (yes my front and backend site share the same .conf, somewhat lazy but also convenient. 

```
<VirtualHost *>
  DocumentRoot /var/www/mydomain-front/checkout/hive-tracking/public/
  ServerName mydomain.com
  ServerAlias www.mydomain.com
  SetEnv _ENV production


        <Directory />
                DirectoryIndex index.phtml
                RewriteEngine On
                Options Indexes FollowSymLinks
                AllowOverride All
        </Directory>




        ErrorLog /var/www/mydomain-front/error.log




        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog /var/www/mydomain-front/access.log combined
</VirtualHost>




<VirtualHost *>
  DocumentRoot /var/www/mydomain-back/checkout/hive-tracking-api/public
  ServerName api.mydomain.com
  SetEnv _ENV production


        <Directory />
                DirectoryIndex index.php
                RewriteEngine On
                Options Indexes FollowSymLinks
        </Directory>




        ErrorLog /var/www/mydomain-back/error.log


        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog /var/www/mydomain-back/access.log combined
</VirtualHost>

```

My .htaccess for the API:

```
RewriteEngine on
ServerSignature On
Options +Indexes +FollowSymlinks
#+MultiViews




#1 YEAR
<FilesMatch "\.(ico|pdf|flv)$">
Header set Cache-Control "max-age=29030400, public"
</FilesMatch>


<FilesMatch "\.(jpg|jpeg|png|gif|swf)$">
Header set Cache-Control "max-age=604800, public"
</FilesMatch>


#1 WEEK
<FilesMatch "\.(xml|txt|css)$">
Header set Cache-Control "max-age=172800, proxy-revalidate"
</FilesMatch>


#2 DAYS
<FilesMatch "\.(html|htm|php|js)$">
Header set Cache-Control "max-age=60, private, proxy-revalidate"
</FilesMatch>


# system/session
RewriteRule ^([-A-Za-z0-9]+)/([-A-Za-z]+)$ index.php?__module=$1&__action=$2 [L,QSA]


RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
```

Going to [http://api.mydomain.com/client](http://api.mydomain.com/client) results in a 404

Any help greatly appreciated!

---


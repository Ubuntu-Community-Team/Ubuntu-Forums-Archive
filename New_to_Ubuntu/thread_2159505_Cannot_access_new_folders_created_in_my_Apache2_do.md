---
title: "Cannot access new folders created in my Apache2 document-root?"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by c3ntury on 2013-07-03
I have tried to create a new folder 'test' in my documentroot of my Apache2 installation, however, whenever I try and access it from a web-browser it gives me a 403 (forbidden) error.



My virtualhosts file -
```
<VirtualHost *:80>
  ServerAdmin webmaster@localhost
  ServerName REMOVED
  DocumentRoot /var/www/


  <Directory />
    Options FollowSymLinks
    AllowOverride All
    AuthType Digest
    AuthName "documentroot"
    AuthDigestProvider file
    AuthUserFile /etc/apache2/htpasswd
    Require user REMOVED
    AllowOverride Indexes
  </Directory>


 <Directory /var/www/>
   Options FollowSymLinks
   Options -Indexes FollowSymLinks MultiViews
   AllowOverride All
   Order allow,deny
   allow from all
 </Directory>


<Directory /var/www/share/>
  Order Deny,Allow
  Allow from all
  Satisfy any
</Directory>


<Directory /var/www/REMOVED/>
    Order Deny,Allow
    Allow from all
    Satisfy any
  </Directory>


  <Directory /var/www/stream/>
    Order Deny,Allow
    Allow from all
    Satisfy any
  </Directory>


   <Directory /var/www/test>
    Order Deny,Allow
    Allow from all
    Satisfy any
 </Directory>


  ErrorLog /var/log/apache2/error.log


  # Possible values include: debug, info, notice, warn, error, crit,
  # alert, emerg.
  
  
  LogLevel warn


  CustomLog /var/log/apache2/access.log combined


  <Directory /var/www/REMOVED>
    AuthType Digest
    AuthName "rutorrent"
    AuthDigestDomain /var/www/REMOVED/ http://46.105.127.19/REMOVED
    AuthDigestProvider file
    AuthUserFile /etc/apache2/htpasswd
    Require valid-user
   SetEnv R_ENV "/var/www/REMOVED"
   AllowOverride Indexes
 </Directory>
</VirtualHost>
    
```

Image of the permissions -
[IMG]http://i.imgur.com/UjRoO0C.png[/IMG]
[B]
Other information -
If I create a new folder (and use chmod --reference to ensure it has the same permissions as an accessible folder), I get a 403 client-side.
If I copy folder 'rapidleech' to the name 'rapidleech1', it will let access 'rapidleech1', but no longer 'rapidleech', until I delete the copy.[/B]
[B]In my logs I found nothing logged in errors.log, and only that it delivered a 403 in access.log.
All the appropriate users are members of www-data.[/B]

---

### Post by sudheesh001 on 2013-07-03
Hi,

This could be because its read-only. You can change the preferences to 777 meaning read-write
If this is the apache server on your ubuntu which you use just for testing. You could modify the permissions of the www-root folder / htdocs folder.

1. cd to the www-root / htdocs using the terminal
2. Run the following command[FONT=courier new]
$ chmod 777 www-root
[/FONT]
3. That should fix up the 403 Forbidden errors, but would leave a security risk in case there are other LAN users
4. You can also change the permissions of a specific folder inside www-root / a specifc file in the same manner.

Hope that helps.

---


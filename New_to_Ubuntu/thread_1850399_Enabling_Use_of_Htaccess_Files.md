---
title: "Enabling Use of Htaccess Files"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by iracida on 2011-09-26
I'm following these directions, [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles), for enabling the use of an htaccess file.

The directions say to add the following lines to /etc/apache2/apache2.conf: 
<Directory /your/path> AllowOverride All </Directory>

However I'm not sure where I should add the code in the apache2.conf file. Should the code go after this section?:

# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

---

### Post by Lisiano on 2011-09-26
AFAIC, htaccess files are enabled already. Try using one in /var/www/ to block viewing the index.html "It works!" page. If not post back and I'll find where the code should go.

---

### Post by iracida on 2011-09-26
It didn't work.

---

### Post by Lisiano on 2011-09-26
Okay you are trying to enable "Password-Protect a Directory With .htaccess"
As per instructions, you can insert the code snippet anywhere you wish, but change "/your/path" to something real.

And if you want to enable .htaccess, change this
```
<Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
</Directory>
```
to this```
<Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
</Directory>
```
AllowOverride is on the 11th line on my system.

Note: I assumed .htaccess was on since the CentOS system I admin had them enabled by default, or I think it did.

---


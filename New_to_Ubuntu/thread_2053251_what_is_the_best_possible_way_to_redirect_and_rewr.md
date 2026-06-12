---
title: "what is the best possible way to redirect and rewrite"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by 007casper on 2012-09-04
what is the best possible way to redirect and rewrite url in virtual host file? 

I prefer to use the redirects in the virtualhost page.  I dont want to use .htaccess... as far as I know that creates too much back and forth.  I want to make sure it is not heavy on the server.

I tried many ways without success.  I am using apache2 + tomcat.  I wonder if it is a cache issue.

I really would like to achieve sub-domains to redirect to a specific page.

such as
user-name.domain.com ----> [www.domain.com/dir/user-name](www.domain.com/dir/user-name)

then, lets say I want to redirect these down below to [www.domain.com](www.domain.com)
w.domain.com
ww.domain.com
[www.www.domain.com](www.www.domain.com)
[www.wwww.domain.com](www.wwww.domain.com)
wwww.domain.com

then, I need to redirect some old pages to the new page.

how would you do it?

I tried several things.  I usually get fail, or warn when I restart apache2.  Even when I get ok on apache2 restart I cant make it work.

```

<IfModule mod_rewrite.c>
   Options +FollowSymLinks
   Options +Indexes
   RewriteEngine On
   RewriteBase /
   RewriteCond %{HTTP_HOST} !www.domain.com$ [NC]
   RewriteCond %{HTTP_HOST} ^(www.)?([a-z0-9-]+).domain.com [NC]
   RewriteRule (.*) %2/$1 [L]
</IfModule> 

```

I tried
```

RewriteEngine On
RewriteCond %{HTTP_HOST} !^domain\.com$
RewriteRule ^/(.*)$ http://www.domain.com/$1 [R=301,L]

```

I tried
```
RedirectMatch 301 (.*) http://www.domain.com$1
```

apache restarted but it failed to redirect it to [www.domain.com](www.domain.com)

here is my virtual host file under /etc/apache2/sites-available

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName [www.domain.com](www.domain.com)
        ServerAlias [www.domain.com](www.domain.com) domain.com
        ServerAlias *.domain.com
        Redirect permanent / [http://www.domain.com](http://www.domain.com)
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>

        ProxyPass / ajp://localhost:8009/
        ProxyPassReverse / ajp://localhost:8009/
</VirtualHost>
```

thank you.

---

### Post by 007casper on 2012-09-05
**bump**

want to do it within virtual host file not in htaccess

---

### Post by 007casper on 2012-09-05
I wonder why redirect doesnt work.

I did...
sudo a2enmod rewrite
sudo /etc/init.d/apache2 restart

still cant get it to work

---

### Post by 007casper on 2012-09-05
I found this link, and follow the instructions.  
[http://developer.mindtouch.com/Deki/FAQ/Configuration/How_do_I...Redirect_Canonical_Hostnames%3f_%28301_Redirection%29](http://developer.mindtouch.com/Deki/FAQ/Configuration/How_do_I...Redirect_Canonical_Hostnames%3f_%28301_Redirection%29)

I restarted the apache2> 
[warn] NameVirtualHost *:80 has no VirtualHosts [ok]

??

domain.com redirects to [www.domain.com](www.domain.com).  I am going to try to redirect the rest of the subdomains and urls

why am I getting the warning?  Is there a better way?


```
NameVirtualHost *
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName [www.domain.com](www.domain.com)
        ServerAlias [www.domain.com](www.domain.com)
        ServerAlias *.domain.com
        Redirect / [http://www.domain.com](http://www.domain.com)
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
        <Proxy *>
        Order deny,allow
        Allow from all
        </Proxy>

        ProxyPass / ajp://localhost:8009/
        ProxyPassReverse / ajp://localhost:8009/
</VirtualHost>

<VirtualHost *>
        RewriteEngine On
        ServerName domain.com
        RedirectMatch 301 ^/(.*) http://www.domain.com/$1
</VirtualHost>

```

---

### Post by 007casper on 2012-09-06
I am using apache2 and tomcat.

I prefer to use the redirects in the virtualhost page.

I really would like to achieve sub-domains to redirect to a specific page.

such as 
user-name.domain.com ----> [www.domain.com/dir/user-name](www.domain.com/dir/user-name)

please advise.  Thank you.

these current settings down below redirects domain.com to [www.domain.com](www.domain.com).  Now, I need to figure out the rest.
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName www.domain.com
	ServerAlias www.domain.com domain.com *.domain.com
	RedirectPermanent / http://www.domain.com
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
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

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
	<Proxy *>
	Order deny,allow
	Allow from all
	</Proxy>
	
	ProxyPass / ajp://localhost:8009/
	ProxyPassReverse / ajp://localhost:8009/
</VirtualHost>
```

---

### Post by 007casper on 2012-09-06
I changed AllowOverride None to AllowOverride All inside the Document Root Directory Directive

still cant make it work.

any ideas ???

[http://ubuntuforums.org/showthread.php?t=1038082](http://ubuntuforums.org/showthread.php?t=1038082)
[http://www.mediacollege.com/internet/server/apache/mod-rewrite/subdomains.html](http://www.mediacollege.com/internet/server/apache/mod-rewrite/subdomains.html)
[http://www.addedbytes.com/articles/for-beginners/url-rewriting-for-beginners/](http://www.addedbytes.com/articles/for-beginners/url-rewriting-for-beginners/)
[http://httpd.apache.org/docs/current/mod/mod_rewrite.html](http://httpd.apache.org/docs/current/mod/mod_rewrite.html)

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName www.domain.com
	ServerAlias www.domain.com domain.com *.domain.com
	RedirectPermanent / http://www.domain.com
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	<IfModule mod_rewrite.c>
                Options +FollowSymLinks
                Options +Indexes	
		RewriteEngine On
		RewriteBase /
		RewriteCond %{HTTP_HOST} !www.domain.com$ [NC]
		RewriteCond %{HTTP_HOST} ^(www.)?([a-z0-9-]+).domain.com [NC]
		RewriteRule (.*) %2/$1 [L]
	</IfModule>	
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
	<Proxy *>
	Order deny,allow
	Allow from all
	</Proxy>
	
	ProxyPass / ajp://localhost:8009/
	ProxyPassReverse / ajp://localhost:8009/
</VirtualHost>
```

---


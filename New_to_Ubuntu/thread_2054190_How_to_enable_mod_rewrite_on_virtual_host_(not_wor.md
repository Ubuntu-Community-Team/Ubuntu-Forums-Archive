---
title: "How to enable mod_rewrite on virtual host (not working?)"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by 007casper on 2012-09-06
I am trying to forward subdomains.  I have tried many things and somehow failing to redirect.
I am using apache2 + tomcat on ubuntu 10.4.  I also have proxy_ajp installed.

I changed AllowOverride None to AllowOverride All for mod_rewrite

so far I have this down below without succes in vhost file> 
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
		RewriteCond %{HTTP_HOST} ^([www.)?(](www.)?()[a-z0-9-]+).domain.com [NC]
		RewriteRule (.*) %2/$1 [L]
		RewriteRule /web/%1
		RewriteRule ^/[0-9]+/[0-9]+/[0-9]+/(.*)?$ /new/blogs/$1 [R=301,NC]
		RewriteRule ^blog/([A-Za-z0-9-]+)(.*)\.html$ /new/blogs/$1 [R=301,NC,L]
	</IfModule>	
	</Directory>

I also tried> 
RewriteCond %{HTTP_HOST} ([^.]+)\.domain.com [NC]
RewriteRule ^(.*) [http://www.domain.com/dir/%1](http://www.domain.com/dir/%1) [P]

without success.

in http.conf 
> 
<IfModule mod_rewrite.c>
     RewriteEngine On
     RewriteLog /private/var/log/apache2/rewrite.log
     RewriteLogLevel 9
</IfModule>

I dont get anything written on the log file, which is weird.

in addition to that, if I put logging in vhost apache2 cant restart. It gives me error on restart.
     RewriteLog /var/log/apache2/rewrite.log
     RewriteLogLevel 9

I need to redirect
domain.com to [www.domain.com](www.domain.com)

and

dir.domain.com ---> [http://www.domain.com/dir/](http://www.domain.com/dir/)
dir.name.domain.com ---> [http://www.domain.com/dir/name](http://www.domain.com/dir/name)

also I would like to redirect old pages to new pages with rewrite rules

RewriteRule ^/[0-9]+/[0-9]+/[0-9]+/(.*)?$ /new/blogs/$1 [R=301,NC]
RewriteRule ^blog/([A-Za-z0-9-]+)(.*)\.html$ /new/blogs/$1 [R=301,NC]

I used these links without any luck.
[http://ubuntuforums.org/showthread.php?t=1038082](http://ubuntuforums.org/showthread.php?t=1038082)
[http://www.mediacollege.com/internet/server/apache/mod-rewrite/subdomains.html](http://www.mediacollege.com/internet/server/apache/mod-rewrite/subdomains.html)
[http://www.addedbytes.com/articles/for-beginners/url-rewriting-for-beginners](http://www.addedbytes.com/articles/for-beginners/url-rewriting-for-beginners)
[http://magicmonster.com/kb/app/apache/neat_urls.html](http://magicmonster.com/kb/app/apache/neat_urls.html)
[http://httpd.apache.org/docs/current/mod/mod_rewrite.html](http://httpd.apache.org/docs/current/mod/mod_rewrite.html)

What am I doing wrong? Here is my current vhost
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName [www.domain.com](www.domain.com)
	ServerAlias [www.domain.com](www.domain.com) domain.com *.domain.com
	RedirectPermanent / [http://www.domain.com](http://www.domain.com)
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
	#	RewriteLog /var/log/apache2/mod_rewrite.log
	#	RewriteLogLevel 9
	#	RewriteBase /
	#	RewriteCond %{HTTP_HOST} !www.domain.com$ [NC]
	#	RewriteCond %{HTTP_HOST} ^([www.)?(](www.)?()[a-z0-9-]+).domain.com [NC]
	#	RewriteRule (.*) %2/$1 [NC]
		RewriteCond %{HTTP_HOST} ([^.]+)\.domain.com [NC]
		RewriteRule ^(.*) [http://www.domain.com/web/%1](http://www.domain.com/web/%1) [P]
	#	RewriteRule /web/%1 [L]
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

Please advise. Thank you so much.

---


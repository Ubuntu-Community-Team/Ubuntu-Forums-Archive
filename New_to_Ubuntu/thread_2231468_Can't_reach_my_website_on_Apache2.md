---
title: "Can't reach my website on Apache2"
date: 2014-06-25
forum: New to Ubuntu
---

### Post by nick120 on 2014-06-25
12.04LTS  Apache2.2.  I am trying to host a simple PLONE site on my Linux box to no avail.

Here is my httpd.conf file (port 80 is blocked by my ISP):

```
# Ensure that Apache listens on port 8082
#Listen 8082


# Listen for virtual host requests on all IP addresses
NameVirtualHost 10.0.1.4:8082


<VirtualHost 10.0.1.4:8082>


<Directory /var/www/Plone>
AllowOverride None
</Directory>




# Other directives here


</VirtualHost>

Here's the sites-available entry:

<VirtualHost 10.0.1.4:8082>
    ServerAdmin webmaster@localhost
        ServerName wiedhas.noip.me
    DocumentRoot /var/www/Plone
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


<Location /var/www/Plone>
      ProxyPass [http://127.0.0.1:8080](http://127.0.0.1:8080)
      ProxyPassReverse [http://127.0.0.1:8080](http://127.0.0.1:8080)
    </Location>


RewriteEngine on
    RewriteRule ^/(.*) http://localhost:8080/VirtualHostBase/http/wiedhas.noip.me/Plone/VirtualHostRoot/$1 [P,L]
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

I can reach my site by "localhost:8080.  When I type the address from NOIP: [http://wiedhas.noip.me](http://wiedhas.noip.me) all I get is 404 "the requested URL / was not found on this server."  Is this a permissions issue or something to do with my setup above?  Thanks in advance for any help.

---

### Post by sameermw on 2014-06-26
did you check your error.log file? And also what about your /etc/hosts file???

127.0.0.1 your_domain_name

---

### Post by yancek on 2014-06-26
The ip addresses you list in your apache configuration file are for local use only.  The link below might help explain the steps needed.

[http://lifehacker.com/124804/geek-to-live--how-to-assign-a-domain-name-to-your-home-web-server](http://lifehacker.com/124804/geek-to-live--how-to-assign-a-domain-name-to-your-home-web-server)

---

### Post by nick120 on 2014-06-26
Thanks for the replies.  Here's my error log file for the last few hours yesterday:
```

[Wed Jun 25 18:24:07 2014] [notice] Apache/2.2.22 (Ubuntu) mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
[Wed Jun 25 18:24:34 2014] [error] [client 97.90.152.45] File does not exist: /etc/apache2/htdocs
[Wed Jun 25 18:24:39 2014] [error] [client 97.90.152.45] File does not exist: /etc/apache2/htdocs
[Wed Jun 25 18:24:50 2014] [error] [client 97.90.152.45] File does not exist: /etc/apache2/htdocs
[Wed Jun 25 18:35:41 2014] [error] [client 97.90.152.45] File does not exist: /etc/apache2/htdocs
[Wed Jun 25 18:35:42 2014] [error] [client 97.90.152.45] File does not exist: /etc/apache2/htdocs
[Wed Jun 25 18:37:27 2014] [error] [client 219.88.66.213] File does not exist: /etc/apache2/htdocs, referer: [http://ubuntuforums.org/showthread.php?t=2231468&p=13058639](http://ubuntuforums.org/showthread.php?t=2231468&p=13058639)
[Wed Jun 25 18:37:27 2014] [error] [client 219.88.66.213] File does not exist: /etc/apache2/htdocs
[Wed Jun 25 18:37:27 2014] [error] [client 219.88.66.213] File does not exist: /etc/apache2/htdocs
[Wed Jun 25 18:39:28 2014] [error] [client 97.90.152.45] File does not exist: /etc/apache2/htdocs
[Wed Jun 25 18:39:47 2014] [notice] caught SIGTERM, shutting down
[Wed Jun 25 18:43:43 2014] [notice] Apache/2.2.22 (Ubuntu) mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
[Wed Jun 25 18:52:08 2014] [notice] caught SIGTERM, shutting down
[Wed Jun 25 18:52:16 2014] [notice] Apache/2.2.22 (Ubuntu) mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
[Wed Jun 25 19:02:19 2014] [notice] SIGUSR1 received.  Doing graceful restart
[Wed Jun 25 19:02:19 2014] [notice] Apache/2.2.22 (Ubuntu) mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
[Wed Jun 25 19:06:53 2014] [notice] SIGUSR1 received.  Doing graceful restart
[Wed Jun 25 19:06:53 2014] [notice] Apache/2.2.22 (Ubuntu) mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
[Wed Jun 25 19:16:38 2014] [notice] SIGUSR1 received.  Doing graceful restart
[Wed Jun 25 19:16:38 2014] [notice] Apache/2.2.22 (Ubuntu) mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
[Wed Jun 25 19:20:07 2014] [notice] SIGUSR1 received.  Doing graceful restart
[Wed Jun 25 19:20:07 2014] [notice] Apache/2.2.22 (Ubuntu) mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
[Wed Jun 25 19:32:25 2014] [notice] SIGUSR1 received.  Doing graceful restart
[Wed Jun 25 19:32:25 2014] [warn] module proxy_module is already loaded, skipping
[Wed Jun 25 19:32:25 2014] [warn] module proxy_http_module is already loaded, skipping
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:8082
no listening sockets available, shutting down
Unable to open logs
[Wed Jun 25 19:50:07 2014] [warn] pid file /var/run/apache2.pid overwritten -- Unclean shutdown of previous Apache run?
[Wed Jun 25 19:50:07 2014] [notice] Apache/2.2.22 (Ubuntu) mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
[Thu Jun 26 11:24:51 2014] [notice] caught SIGTERM, shutting down
[Thu Jun 26 11:25:03 2014] [notice] Apache/2.2.22 (Ubuntu) mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
```

I am totally confused about how to set up Apache to point to my Plone site at /var/www/Plone.  I have noip set up and forwarding port 8082 to the linux box.  All I get is the main page of my Plone site with all of the html links pointing to localhost:8080.  The page seems broken as it is not rendered correctly at all - images are broken etc.  Should I erase all of the info in httpd.conf and redo my vhost file in sites-available?  I have no /etc/hosts file.  Didn't know I needed one.  How would this help?

---

### Post by yancek on 2014-06-26
I'm curious as to where the error about:  File does not exist: /etc/apache2/htdocs

Since there is not htdocs directory used in Ubuntu.  Some distributions use /var/www/htdocs, others /var/www/html and Ubuntu just /var/www.  You can of 
course create sub-directories here.  You need to register a domain name.

---

### Post by nick120 on 2014-06-26
I have a registered domain name: wiedhas.noip.me.  It points to my IP address using port 8082 which is routed to my Linux box.  I can't for the life of me figure out how to configure apache to serve my /var/www/Plone site.  I am following the directions here [http://docs.plone.org/manage/deploying/front-end/apache.html#installing-apache-front-end-for-plone](http://docs.plone.org/manage/deploying/front-end/apache.html#installing-apache-front-end-for-plone) .  Do I need to set this: [COLOR=#333333][FONT=Menlo]ServerAlias yoursite.com[/FONT][/COLOR]    ServerSignature On
as "wiedhas.noip.me"

and set this: RewriteEngine on    RewriteRule ^/(.*) http://localhost:8080/VirtualHostBase/http/yoursite.com:80/Plone/VirtualHostRoot/$1 [P,L]

to: http://localhost:8080/VirtualHostBase/http/wiedhas.noip.me:8082/Plone/VirtualHostRoot/$1 [P,L] ??

I can reach my linux box from the internet, but I am having a problem serving all of the files in the Plone directory.  Perhaps this is an error with my Plone setup and something called virtualhostmonster.

---


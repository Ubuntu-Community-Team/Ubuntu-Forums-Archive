---
title: "apache rewrite rule not working"
date: 2015-10-12
forum: New to Ubuntu
---

### Post by bluethundr2 on 2015-10-12
Hey guys,

I have an apache rewrite rule that I'm having difficulty getting to work. The problem I'm having exists only under ubuntu however, as I'm using a nearly identical rewrite rule in CentOS that works perfectly. So I'm having a hard time understanding why the one I'm using under ubuntu 14.04 isn't working at all. 

Here's the rewrite rule I have in ubuntu apache2:

```
                RewriteEngine  on
                RewriteRule    "^/$"  "/superldap" [PT]

```

And here's the one I have in CentOS 7:

```
               RewriteEngine  on
               RewriteRule    "^/$"  "/nagios" [PT]

```

Pretty much identical. right? Both are in SSL vhosts on their repsective platforms. If I go to the nagios machine on / it takes me right to the /nagios URL as desired. However if I go to / on the ldap machine, instead of redirecting me to the /superldap URL, it just sits there on /.

If I refresh the page on ubuntu, this is all I see in the logs:

```
2454.101 Safari/537.36"
47.18.111.100 - - [13/Oct/2015:00:37:11 +0000] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://ldap1.example.com/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36"
47.18.111.100 - - [13/Oct/2015:00:37:12 +0000] "GET / HTTP/1.1" 200 3593 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36"
47.18.111.100 - - [13/Oct/2015:00:37:12 +0000] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://ldap1.example.com/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36"
47.18.111.100 - - [13/Oct/2015:00:42:01 +0000] "GET / HTTP/1.1" 200 3594 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36"
47.18.111.100 - - [13/Oct/2015:00:42:01 +0000] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://ldap1.example.com/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36"
47.18.111.100 - - [13/Oct/2015:00:42:01 +0000] "GET / HTTP/1.1" 200 3593 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36"
47.18.111.100 - - [13/Oct/2015:00:42:02 +0000] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://ldap1.example.com/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36"


```

And I see NO activity in the error logs when refreshing the page!!

For comparison, here are the two SSL apache vhosts.

This is the non-redirecting SSL vhost in ubuntu:

```
#egrep -v "^$|^(.*)#"  /etc/apache2/sites-enabled/default-ssl.conf
<IfModule mod_ssl.c>
        <VirtualHost _default_:443>
                ServerAdmin bluethundr@somewherel.com
                ServerName ldap1.example.com
                DocumentRoot /var/www/html
                ErrorLog ${APACHE_LOG_DIR}/error.log
                CustomLog ${APACHE_LOG_DIR}/access.log combined
                SSLEngine on
                SSLCertificateFile /etc/apache2/ssl/apache.crt
                SSLCertificateKeyFile /etc/apache2/ssl/apache.key
                <FilesMatch "\.(cgi|shtml|phtml|php)$">
                                SSLOptions +StdEnvVars
                </FilesMatch>
                <Directory /usr/lib/cgi-bin>
                                SSLOptions +StdEnvVars
                </Directory>
                BrowserMatch "MSIE [2-6]" \
                                nokeepalive ssl-unclean-shutdown \
                                downgrade-1.0 force-response-1.0
                BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
                <Location /superldap>
                 AuthType Basic
                 AuthName "Restricted Files"
                 AuthUserFile /etc/apache2/htpasswd
                 Require valid-user
               </Location>


                RewriteEngine  on
                RewriteRule    "^/$"  "/superldap" [PT]
        </VirtualHost>
</IfModule>

```

And this, for comparison is the one that works under CentOS 7:

```

 #egrep -v "^$|^#"  002_naigos.ssl.conf
Listen 443
<VirtualHost *:443>
   ServerName nagios.example.com
   ServerAlias monitor1.example.com
   CustomLog /var/log/httpd/monitor1.example.com.log combined
   ErrorLog /var/log/monitor1.example.com-error.log
   LogLevel warn
   SSLEngine on
   SSLProtocol all -SSLv2
   SSLCipherSuite ALL:!ADH:!EXPORT:!SSLv2:RC4+RSA:+HIGH:MEDIUM:+LOW
   SSLCertificateFile /etc/httpd/ssl/monitor1.jokefire.com.crt
   SSLCertificateKeyFile /etc/httpd/ssl/monitor1.jokefire.com.key
ScriptAlias /nagios/cgi-bin "/usr/local/nagios/sbin"
<Directory "/usr/local/nagios/sbin">
   Options ExecCGI
   AllowOverride None
   <IfVersion >= 2.3>
      <RequireAll>
         Require all granted
         AuthName "Nagios Access"
         AuthType Basic
         AuthUserFile /etc/nagios/htpasswd.users
         Require valid-user
      </RequireAll>
   </IfVersion>
   <IfVersion < 2.3>
      Order allow,deny
      Allow from all
      AuthName "Nagios Access"
      AuthType Basic
      AuthUserFile /etc/nagios/htpasswd.users
      Require valid-user
   </IfVersion>
</Directory>
Alias /nagios "/usr/local/nagios/share"
<Directory "/usr/local/nagios/share">
   Options None
   AllowOverride None
   <IfVersion >= 2.3>
      <RequireAll>
         Require all granted
         AuthName "Nagios Access"
         AuthType Basic
         AuthUserFile /etc/nagios/htpasswd.users
         Require valid-user
      </RequireAll>
   </IfVersion>
   <IfVersion < 2.3>
      Order allow,deny
      Allow from all
      AuthName "Nagios Access"
      AuthType Basic
      AuthUserFile /etc/nagios/htpasswd.users
      Require valid-user
   </IfVersion>
</Directory>
RewriteEngine  on
RewriteRule    "^/$"  "/nagios" [PT]
</VirtualHost>

```

Can someone please clue me into why this setup isn't working under Ubuntu?

Thanks

---

### Post by Lars Noodén on 2015-10-13
Are you missing the [LoadModule](http://httpd.apache.org/docs/2.4/mod/mod_so.html#loadmodule) directive?  In Ubuntu the usual way to enable it is with the following two steps.

```

sudo a2enmod rewrite 
sudo service apache2 restart

```

---

### Post by SeijiSensei on 2015-10-13
I suspect it's the problem Lars is referring to, that mod_rewrite is not being loaded.  CentOS tends to load more modules by default than Ubuntu does in my experience.

If your server supports PHP, it's always handy to have a little script to display the results of phpinfo():
```

cd /var/www/html
sudo echo '<?php phpinfo() ?>' > phpinfo.php

```
A request for [http://localhost/phpinfo.php](http://localhost/phpinfo.php) will report back a dizzying array of information about both the Apache and PHP configurations.

---

### Post by bluethundr2 on 2015-10-13
> **SeijiSensei said:**
> I suspect it's the problem Lars is referring to, that mod_rewrite is not being loaded. CentOS tends to load more modules by default than Ubuntu does in my experience.

If your server supports PHP, it's always handy to have a little script to display the results of phpinfo():
```

cd /var/www/html
sudo echo '<?php phpinfo() ?>' > phpinfo.php

```
A request for [http://localhost/phpinfo.php](http://localhost/phpinfo.php) will report back a dizzying array of information about both the Apache and PHP configurations.


Hey guys,

 That's a reasonable thought that mod_rewite wasn't enabled. But it was:

```
[root@ldap1:~] #a2enmod rewrite
Module rewrite already enabled


[root@ldap1:~] #apachectl -M | grep rewrite
 rewrite_module (shared)

``` 

Probably should've mentioned that in the original post. That's why I'm so baffled this isn't working. Any other thoughts there?

Also I just setup a php info page on this server, and attached it to the post, in case that helps.

---

### Post by SeijiSensei on 2015-10-13
If you're always going to rewrite the root URI to /superldap, why not just make /var/www/html/superldap, or /path/to/superldap if it's located somewhere else, the DocumentRoot and avoid rewriting entirely?  

One other difference I see is the use of <Directory> in the CentOS configuration and <Location> in the other. I don't know if that has anything to do with the rewriting issue.

---

### Post by jim_deadlock on 2015-10-13
I would first ensure that mod_rewrite is actually working by using a very simple rewrite rule such as:

```
RewriteEngine  on
RewriteBase /
RewriteRule .* http://yourdomain.com/testpage.html
```

If that works then you can rule out a problem with mod_rewrite and concentrate on your rule syntax. It may be a case of needing a full URL or something like that.

---

### Post by Habitual on 2015-10-13
Maybe enable/configure mod_rewrite logging?
See [https://httpd.apache.org/docs/current/mod/mod_rewrite.html](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) for details...

---

### Post by bluethundr2 on 2015-10-17
> **Habitual said:**
> Maybe enable/configure mod_rewrite logging?
See [https://httpd.apache.org/docs/current/mod/mod_rewrite.html](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) for details...

Hi, thanks for that tip! I did set this up in my apache configuration:

```
                ErrorLog ${APACHE_LOG_DIR}/error.log
                CustomLog ${APACHE_LOG_DIR}/access.log combined
                LogLevel alert rewrite:trace3

``` 


And this is all I see in the access log after restarting apache with that configuration set:

```
47.18.111.100 - - [17/Oct/2015:20:56:56 +0000] "GET / HTTP/1.1" 200 3593 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:20:56:56 +0000] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://ldap1.example.com/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:20:59:57 +0000] "GET / HTTP/1.1" 200 3594 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:20:59:57 +0000] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://ldap1.example.com/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:20:59:58 +0000] "GET / HTTP/1.1" 200 3593 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:20:59:58 +0000] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://ldap1.example.com/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:20:59:59 +0000] "GET / HTTP/1.1" 200 3593 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:20:59:59 +0000] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://ldap1.example.com/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:20:59:59 +0000] "GET / HTTP/1.1" 200 3593 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:20:59:59 +0000] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://ldap1.example.com/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:21:00:00 +0000] "GET / HTTP/1.1" 200 3593 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"
47.18.111.100 - - [17/Oct/2015:21:00:00 +0000] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://ldap1.example.com/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36"

```

And this is all I see in the error logs:

```
[Sat Oct 17 20:53:01.988318 2015] [mpm_prefork:notice] [pid 651] AH00169: caught SIGTERM, shutting down
[Sat Oct 17 20:53:03.023343 2015] [ssl:warn] [pid 20393] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Sat Oct 17 20:53:03.055347 2015] [ssl:warn] [pid 20402] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Sat Oct 17 20:53:03.057003 2015] [mpm_prefork:notice] [pid 20402] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.13 OpenSSL/1.0.1f configured -- resuming normal operations
[Sat Oct 17 20:53:03.057021 2015] [core:notice] [pid 20402] AH00094: Command line: '/usr/sbin/apache2'
[Sat Oct 17 20:56:08.778086 2015] [mpm_prefork:notice] [pid 20402] AH00169: caught SIGTERM, shutting down
[Sat Oct 17 20:56:09.839871 2015] [mpm_prefork:notice] [pid 20710] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.13 OpenSSL/1.0.1f configured -- resuming normal operations
[Sat Oct 17 20:56:09.839907 2015] [core:notice] [pid 20710] AH00094: Command line: '/usr/sbin/apache2'

```

And I don't find anything relating to this problem oddly.

It's a weird one. I can't imagine why the centos rewrite rule would work and the one under ubuntu wouldn't. They're almost the same! And we're still dealing with apache 2 on both platforms.

Any more ideas? I'd still prefer to solve this using a rewrite rule.

---


---
title: "Using proxy_ajp with Apache2 and Jboss"
date: 2007-08-27
forum: Programming Talk
---

### Post by Howler9443 on 2007-08-27
Hello everyone,

I am having a couple of issues. I have setup Apache2 and Jboss. Each works as expected in standalone mode.

For testing purposes I have Apache2 setup on port 150. JBoss is on the default port 8080

I have enabled mod_proxy and proxy_ajp using a2enmod

my 000-default site config is as follows

```



NameVirtualHost *

<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    ProxyPass /myapp ajp://localhost:8009/myapp
    ProxyPassReverse /myapp ajp://localhost:8009/myapp

</VirtualHost>



```

When attempting to access 'myapp' I get the following error

```

Forbidden

You don't have permission to access /myapp on this server.
Apache/2.2.3 (Ubuntu) mod_jk/1.2.18 PHP/5.2.1 Server at yourhost.homelinux.net Port 150


```

Any suggestions as to what I can do to resolve this?

Thanks.

---

### Post by Howler9443 on 2007-08-27
Ok, I resolved this issue.

I was starting Jboss in the following way...

$>./run.sh -c prod --host=192.168.1.100

I was doing this so that I could remotely access the JBoss console from within my home network without setting up the proxy until I was ready. By default JBoss binds to the localhost address as defined in the /etc/hosts file

I stopped JBoss and restarted without the --host parameter and my proxies began to work without issue.

So here is the breakdown of how I use proxy_ajp with JBoss 4.2.0-GA with Ubuntu 7.04

[LIST=1]
[*]Install proxy_ajp

```
$> sudo a2enmod proxy_ajp
```

[*]Modify /etc/apache2/mods-enabled

*** *WARNING YOU DO THIS AT YOUR OWN RISK...YOU HAVE BEEN WARNED****

Change the line **"Deny from all" **to **"Allow from all" **

if you are opening this up to the web and not just an intranet. If you want this on the intranet only provide your host such as **"Allow from .myhost.com" **(Yes thats a period in front of myhost)  This prevents the "Forbidden" error message since this now allows proxies to be used.

[*]Modify /etc/apache2/sites-enabled/000-default (or whatever site you have set up)

Add lines to proxy to your webapp
```

ProxyPass /mywebapp ajp://localhost:8009/mywebapp
ProxyPassReverse /mywebapp [***]ajp://localhost:8009/mywebapp

```
[*]Port 8009 is the default AJP port for JBoss if you have configured other instances of JBoss you will have to change the port accordingly.

[*]Restart Apache2 and make sure JBoss is up and running.

[*] ```
 $>sudo /etc/init.d/apache2 restart
```
[/LIST]

Hopefully that should do it.

I just wanted to document this procedure for future reference as I know I will just totally forget it! ;-P

---


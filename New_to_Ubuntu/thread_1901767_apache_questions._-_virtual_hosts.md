---
title: "apache questions. - virtual hosts?"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by kristiaan_d on 2011-12-29
Hi Guys,
im getting my head around Apache at the moment and need some advice, i have a linux box that is running nagios to monitor systems for me, however when you goto the servers IP address it comes up with the default IT WORKS! page, if i then put a sub folder onto the end of the ip address i.e. /Nagios/ it loads the Nagios interface.

in the conf.d folder there is a nagios.conf file and in there is the code i was looking for (as it wasnt in the default file in sites-available), my question is, rather than have that code in there can i put it into the virtualhost's conf file in the sites-available folder? 

the reason i want to-do this to help keep things easier to remember i want to setup a sub-domain so that when you hit that subdomain it goes directly to the nagios folder.

so at the moment my virtualhost config looks like this

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

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

</VirtualHost>

```

 and my nagios conf file looks like this,

```

ScriptAlias /nagios/cgi-bin "/usr/local/nagios/sbin"

<Directory "/usr/local/nagios/sbin">
#  SSLRequireSSL
   Options ExecCGI
   AllowOverride None
   Order allow,deny
   Allow from all
#  Order deny,allow
#  Deny from all
#  Allow from 127.0.0.1
   AuthName "Nagios Access"
   AuthType Basic
   AuthUserFile /usr/local/nagios/etc/htpasswd.users
   Require valid-user
</Directory>

Alias /nagios "/usr/local/nagios/share"

<Directory "/usr/local/nagios/share">
#  SSLRequireSSL
   Options None
   AllowOverride None
   Order allow,deny
   Allow from all
#  Order deny,allow
#  Deny from all
#  Allow from 127.0.0.1
   AuthName "Nagios Access"
   AuthType Basic
   AuthUserFile /usr/local/nagios/etc/htpasswd.users
   Require valid-user
</Directory>
```


am i correct in thinking i can merge the two config files so they look like this?


```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

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

    ScriptAlias /nagios/cgi-bin "/usr/local/nagios/sbin"

    <Directory "/usr/local/nagios/sbin">
    #  SSLRequireSSL
       Options ExecCGI
       AllowOverride None
       Order allow,deny
       Allow from all
    #  Order deny,allow
    #  Deny from all
    #  Allow from 127.0.0.1
       AuthName "Nagios Access"
       AuthType Basic
       AuthUserFile /usr/local/nagios/etc/htpasswd.users
       Require valid-user
    </Directory>

    Alias /nagios "/usr/local/nagios/share"

    <Directory "/usr/local/nagios/share">
    #  SSLRequireSSL
       Options None
       AllowOverride None
       Order allow,deny
       Allow from all
    #  Order deny,allow
    #  Deny from all
    #  Allow from 127.0.0.1
       AuthName "Nagios Access"
       AuthType Basic
       AuthUserFile /usr/local/nagios/etc/htpasswd.users
       Require valid-user
    </Directory>

</VirtualHost>
```

---

### Post by kristiaan_d on 2011-12-30
quick bump in the hope that someone sees this and has a idea

---


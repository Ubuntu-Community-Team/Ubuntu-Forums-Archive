---
title: "Ubuntu Apache2 Virtualhost visible on entire LAN"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by mike_abc on 2012-03-12
[SIZE=2]Hi,

I have installed LAMP on [/SIZE][SIZE=2]Ubuntu 10.04 [/SIZE][SIZE=2] for WEBSITE DEVELOPMENT on my main workstation which I regard as a "server". On this machine (192.168.1.2), the site works using **localhost**.

Now I would like to be able to access my development website from all computers which are connected to the same LAN (192.168.1.xxx).

How should my **sites-available, sites-enabled** and - if needed, **httpd.conf (and any other files, for that matter) -** be changed so that this happens ? [COLOR=Purple]**I don't have a REAL www domain name**[/COLOR] and only want to be able to see my development website from the other computers on my LAN thru a browser.


Thanks in advance for any feedback.

Mike

 


[/SIZE]

---

### Post by mike_abc on 2012-03-13
[SIZE=2]My Apache2 config files are as follows:

httpd.conf - nothing

**default** in **sites-available** contains:

[/SIZE]```

[SIZE=2]<VirtualHost *:80>
    ServerName localhost
    DocumentRoot /var/www
</VirtualHost>

# Setup "whateverhost.tld" Virtual Host

<VirtualHost *:80>
    ServerName floraro.tld
    DocumentRoot /var/www/FloraRO/htdocs

    <Directory /var/www/FloraRO/htdocs>
        Options Indexes FollowSymLinks Includes
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>
[/SIZE]
```[SIZE=2]

**sites-enabled** contains a link named **floraro.tld** after I used the "a2ensite default" command.

I keep getting the "Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" error when I start the Apache Server.

Mike

[/SIZE]

---

### Post by alphacrucis2 on 2012-03-13
You could add a host name to the hosts file on your pc's. In linux it is just 

/etc/hosts


You add a line like:

192.168.1.5     myhost.xyz

or 

192.168.1.5     [www.somehost.faketld](www.somehost.faketld)

etc

That's how it was done before the DNS existed.


You can even do it in Windows. The file is usually called

c:\Windows\system32\drivers\etc\hosts


On Windows it is a common tactic of viruses to add fake entries in the hosts file to redirect web browsers.

---

### Post by Bobhuber on 2012-03-13
> **mike_abc said:**
> [SIZE=2]My Apache2 config files are as follows:

httpd.conf - nothing

**default** in **sites-available** contains:

[/SIZE]```

[SIZE=2]<VirtualHost *:80>
    ServerName localhost
    DocumentRoot /var/www
</VirtualHost>

# Setup "whateverhost.tld" Virtual Host

<VirtualHost *:80>
    ServerName floraro.tld
    DocumentRoot /var/www/FloraRO/htdocs

    <Directory /var/www/FloraRO/htdocs>
        Options Indexes FollowSymLinks Includes
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>
[/SIZE]
```[SIZE=2]

**sites-enabled** contains a link named **floraro.tld** after I used the "a2ensite default" command.

I keep getting the "Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" error when I start the Apache Server.

Mike

[/SIZE]
echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---


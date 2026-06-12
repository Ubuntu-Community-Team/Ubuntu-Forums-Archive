---
title: "generic localhosts question"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-06-05
Does anyone know how to configure virtual hosts so that you can load a website running on your computer (localhost) on any computer in the local network?
I'm at my school right now with my website on my laptop (which has apache2 installed) and I need to present the website I've been working on this semester.  I can't put it on the school's computer for the presentation because they don't have php or mysql installed (most of the semester is learning about HTML and flash).  I'm currently connected on my laptop to the school's wireless (I can connect to their network through the LAN if needed).

---

### Post by Oldsoldier2003 on 2008-06-05
> **fontenot_1031 said:**
> Does anyone know how to configure virtual hosts so that you can load a website running on your computer (localhost) on any computer in the local network?
I'm at my school right now with my website on my laptop (which has apache2 installed) and I need to present the website I've been working on this semester.  I can't put it on the school's computer for the presentation because they don't have php or mysql installed (most of the semester is learning about HTML and flash).  I'm currently connected on my laptop to the school's wireless (I can connect to their network through the LAN if needed).

if your apache server is running any you haven't closed the ports using iptables or UFW then anyone on the lan should be able to connect to you by your ip address.

---

### Post by fontenot_1031 on 2008-06-05
> **Oldsoldier2003 said:**
> if your apache server is running any you haven't closed the ports using iptables or UFW then anyone on the lan should be able to connect to you by your ip address.
I currently don't even have a firewall on my computer running.  I suppose it could be a closed port on the school's internet though :(

```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /wwwroot/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /wwwroot/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /wwwroot/cgi-bin/
        <Directory "/wwwroot/cgi-bin">
                AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
                AddHandler cgi-script cgi pl py pyc
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

</VirtualHost>

```

---


---
title: "wordpress *:80 has no VirtualHosts"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by picante62 on 2012-02-13
**NameVirtualHost *:80 has no VirtualHosts**             
                                                                I recently  purchased Kyle Rankin's The Official ubuntu Server Book and am trying to  install a wordpress site by following the directions he provides. 

I'm using 10.4 on Amazon AWS. 
As sudo I: 
install and update the server.
install LAMP via tasksel
apt-get install wordpress
create configuration file in /etc/apache2/sites-available/wordpress with the following configuration:

NameVirtualHost *:80

    <VirtualHost *:80>
    UseCanonicalName    Off
    VirtualDocumentRoot /var/www/%0
    Options All
    </VirtualHost>

a2ensite wordpress 
a2dissite default
a2enmod vhost_alias
sudo ln -s /usr/share/wordpress/  var/mydomainename.com
service apache2 restart

run the script:
bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress mydomainname.com

I get the following error message:

[Tue Feb 07 21:50:28 2012] [error] (EAI 2)Name or service not known: Could not resolve host name *.80 -- ignoring!
[Tue Feb 07 21:50:28 2012] [warn] NameVirtualHost *:80 has no VirtualHosts

When I try in ipaddress or domain name I get:

Not Found

The requested URL / was not found on this server.

I was hoping someone could offer suggestions to get wordpress running.

Thanks

---

### Post by lechien73 on 2012-02-13
If you check the contents of the /etc/apache2/ports.conf file, do you also have NameVirtualHost *:80 ?

If so, edit ports.conf and comment out that line.

Restart apache:

```
service apache2 restart
```

and try your script again :)

---


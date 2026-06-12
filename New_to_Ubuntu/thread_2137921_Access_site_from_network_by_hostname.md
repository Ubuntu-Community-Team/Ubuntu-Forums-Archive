---
title: "Access site from network by hostname"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by dimaomni on 2013-04-22
Hi 

I use Ubuntu 12.10.
I read a lot of information and as result I have become more confused. 
I have installed Apache, MySQL, PHP and phpMyAdmin successfully. And I can access my site from local network by 192.168.190.17.
[B]How can I do access via alias as "buro" or smth like it from LAN.
[/B]
Should I configured bind9 or just correct cinfigure Virtual Hosts?

I tried to edit /etc/hosts, added virtual host
/etc/hostname  
```

websrv

/etc/hosts           
127.0.0.1       localhost buro
#192.168.190.17  buro
192.168.190.17  websrv
#192.168.180.17 websrv 

```
/etc/nsswitch.conf
```

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis       

```

/etc/apache2/sites-available/default
```

<VirtualHost *:80>
        ServerName buro
        ServerAlias buro

        DocumentRoot /var/www
        ErrorLog /var/www/error.log
        CustomLog /var/www/access.log common

</VirtualHost>  

```
```

root@websrv:~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.190.17 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name,
using 192.168.190.17 for ServerName
   ...done.     

root@websrv:/etc/apache2/sites-available# sudo a2ensite buro
ERROR: Site buro does not exist!      

root@websrv:/etc/apache2/sites-available# ping buro
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.038 ms  

```
From another PC cannot ping by hostname.

/etc/apache2/apache2.conf  - This config I left without any change.

---

### Post by schragge on 2013-04-22
The simplest way is to add buro to /etc/host *on the PC you want to access it from*
```
192.168.190.17  buro
```

---

### Post by sanderj on 2013-04-22
Between Ubuntu machines, you can use "<hostname>.local.".

For example:

```
sander@hapee:~$ ping flappie.local.
PING flappie.local. (192.168.0.101) 56(84) bytes of data.
64 bytes from flappie.local (192.168.0.101): icmp_req=1 ttl=64 time=7.59 ms
64 bytes from flappie.local (192.168.0.101): icmp_req=2 ttl=64 time=3.15 ms
```

HTH

---

### Post by dimaomni on 2013-04-22
as you see in host I have already added. I commended it as it didn't resolve issue

#192.168.190.17  buro

---

### Post by schragge on 2013-04-22
Sorry, I misunderstood what you did. I thought you added it to */etc/hosts* on the machine you want to access to, i.e. on buro itself which is obviously wrong.

---

### Post by kuifje09 on 2013-04-22
Does your firewall allow connections from outside world?  I mean, ping is not enough. must have allowed port 80.

---

### Post by SeijiSensei on 2013-04-22
Entries that begin with a "hash" mark ("#") are comments and thus ignored by nearly all programs in the Linux world.  The entry 
```
#192.168.190.17 buro 
```
is no different from having no entry at all.  Remove the hash mark.

Also you might be able to tell your router to advertise buro as a hostname via DNS.  Browse around your router settings and see if that's possible.  Better yet, give the machine a static IP address so it will always have the same hostname-to-IP mapping.

---


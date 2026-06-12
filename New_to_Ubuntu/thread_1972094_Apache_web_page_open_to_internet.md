---
title: "Apache web page open to internet"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by lazyminion on 2012-05-03
Hello,

I'm having issues making an apache page accessible over the internet.

Server: Ubuntu Server 11.10, Apache 2.2

I have registered a domain with dyn.com and have ddclient setup and seems to be working... (Externally i do a nslookup and shows my routers IP, ping does not work I thought it did once but unsure…)

Port forwarding is enabled on router pointing to server for port: 80..

No firewall enabled ATM.

I know the domain is linked to my server since I installed “Webmin” and can access “Webmin” fine externally via the domain name and the port.
Have a virtual host enabled on Apache listening on port 80, the apache site is accessible via the intranet so without updating my host file on another PC the domain will work and open the index file.

What do I need to do to make the site available on the internet…..????

I contacted my ISP and made sure that port 80 is not blocked....
Optus advised that the only port they block is 25...

Check routers remote management section and router page is hosted on port 8080 so this is not effecting the site. (Also enabled remote management just to test accessing the router via "Mydomain".com:8080, worked fine...)

Please let me know what information you require for trouble shooting… 

Happy Regards,
Ryan

---

### Post by lazyminion on 2012-05-06
Well if anyone else had this issue and was confused i think it may just be the ISP blocking port 80.....

I havnt got it confirmed since the tech support from Optus suck and some don't even know what a port is... but yeah..

[http://forums.whirlpool.net.au/archive/1885300](http://forums.whirlpool.net.au/archive/1885300)

---

### Post by llamabr on 2012-05-06
[http://taufanlubis.wordpress.com/2007/10/20/ip-and-port-scanning-using-nmap-network-mapper-in-ubuntu/](http://taufanlubis.wordpress.com/2007/10/20/ip-and-port-scanning-using-nmap-network-mapper-in-ubuntu/)

---

### Post by lazyminion on 2012-05-06
Wont that just scan my network to see which ports i have open on my router... not what ports my ISP has open...

---

### Post by ammofreak on 2012-05-07
Hi ):P
You have no firewall enabled on the server. You are able to access Webmin externally. You are not successful in pinging because for some reason the server is not responding (your router config is directing the ping ICMP to your server). I would therefore start by looking at /etc/apache2/ports.conf to see what port(s) the server is listening to.

---

### Post by lazyminion on 2012-05-07
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```


Within sites enabled i do not have the file "000-default" sorry don't have much experience with apache and unsure if this file is needed.... if it is what would it contain?

---


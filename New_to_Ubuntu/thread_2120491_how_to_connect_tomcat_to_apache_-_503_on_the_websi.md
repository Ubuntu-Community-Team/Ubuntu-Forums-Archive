---
title: "how to connect tomcat to apache - 503 on the website via ajp"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by 007casper on 2013-02-26
I am getting 503 on my website.  I am trying to connect tomcat with apache.  I tried several things.  I cant seem to make it work.

I have enabled a2enmod
a2enmod proxy_ajp
a2enmod proxy
a2enmod proxy_http
a2enmod ssl

first error I was getting...
> proxy:ajp 'client denied by server configuration'

I was getting forbidden on the browser, I played with apache settings, and checked... 

grep -r 'Connector port="8009"' *

Then, I have added address="127.0.0.1" on tomcat6 server.xml
> 
<Connector port="8009" address="127.0.0.1" protocol="AJP/1.3" redirectPort="8443"/>

cd /var/log/apache2 cat error.log

now, I am getting this error...
> 
[Tue Feb 26 12:46:47 2013] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Tue Feb 26 12:46:47 2013] [error] proxy: AJP: failed to make connection to backend: localhost
[Tue Feb 26 12:52:15 2013] [error] (111)Connection refused: proxy: AJP: attempt to connect to 127.0.0.1:8009 (localhost) failed
[Tue Feb 26 12:52:15 2013] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Tue Feb 26 12:52:15 2013] [error] proxy: AJP: failed to make connection to backend: localhost

ps ax | grep httpd | wc -l
>  1 

please advise

Thank you.

---

### Post by slickymaster on 2013-02-26
See if this helps you:

[Connecting Apache Web Server to Tomcat and writing re-direct rules]("http://community.jaspersoft.com/wiki/connecting-apache-web-server-tomcat-and-writing-re-direct-rules")

---

### Post by 007casper on 2013-02-27
thank you for that link.

I still have the same problem.  

cd /var/log/apache2 cat error.log

[Wed Feb 27 15:14:22 2013] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Wed Feb 27 15:14:22 2013] [error] proxy: AJP: failed to make connection to backend: localhost
[Wed Feb 27 15:14:24 2013] [error] (111)Connection refused: proxy: AJP: attempt to connect to 127.0.0.1:8009 (localhost) failed
[Wed Feb 27 15:14:24 2013] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Wed Feb 27 15:14:24 2013] [error] proxy: AJP: failed to make connection to backend: localhost


cat mod_jk.log
[Wed Feb 27 15:14:17.290 2013] [8687:3074295552] [error] uri_worker_map_ext::jk_uri_worker_map.c (506): Could not find worker with name 'jk-manager' in uri map post processing.
[Wed Feb 27 15:14:17.290 2013] [8687:3074295552] [error] uri_worker_map_ext::jk_uri_worker_map.c (506): Could not find worker with name 'jk-status' in uri map post processing.

---

### Post by 007casper on 2013-03-01
I stil get the same error...

flushed iptables
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F
sudo iptables -X

a2enmod proxy_ajp
a2enmod proxy
a2enmod proxy_http
a2enmod ssl
a2enmod rewrite

/etc/apache2/sites-available
enable store.example.com-ssl

make sure store.example.com-ssl have ssl-certficate, ssl-key, ssl-bundle(from vendor)

/etc/init.d/apache2 reload
/etc/init.d/apache2 restart

apache2ctl configtest

apache2ctl restart

site doesnt load.  Check the apache2 error.log same error.

[Fri Mar 01 03:55:30 2013] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Fri Mar 01 03:55:30 2013] [error] proxy: AJP: failed to make connection to backend: localhost
[Fri Mar 01 14:32:06 2013] [error] (111)Connection refused: proxy: AJP: attempt to connect to 127.0.0.1:8009 (localhost) failed

---


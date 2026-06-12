---
title: "HOWTO:  qBittorrent WebUI + Apache (with notes on utorrent)"
date: 2010-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by onemyndseye on 2010-10-05
I spent days beating my head against the desk trying to make this work so I thought i would share :)


My need was to block everything but localhost access to qbitt's WebUI and make it available as /torrent/ on my local apache web server.  I used mod_proxy to make this work.

First off we will need both mod_proxy and mod_xml2enc...


For mod_proxy:
```

sudo apt-get install libapache2-mod-proxy-html

```

For mod_xml2enc
```

sudo apt-get install apache2-prefork-dev
mkdir ~/modbuild/ && cd ~/modbuild/
wget http://apache.webthing.com/svn/apache/filters/mod_xml2enc.c
wget http://apache.webthing.com/svn/apache/filters/mod_xml2enc.h
apxs2 -aic -I/usr/include/libxml2 ./mod_xml2enc.c
cd ~
rm -rfd ~/modbuild/
sudo service apache2 restart

```


Now for the apache configs.   There are many many ways to do this and keep in mind this is deployed on a small intranet with only small needs for security.  I would enjoy hearing tips from others about access control to the /torrent/ location.  The following must be added to an existing vhost (my use case) or to a newly created one as it will not work outside of VirtualHost directives...

The basic config for qbitt's WebUI commented for clarity.
```

  ProxyRequests off
  <Proxy *>
      allow from all
  </Proxy>

  ## We need to transpose requests to WebUI's command scripts 
  ## to the new location /torrent/command and feed it through 
  ## the proxy denoted by [P]
  RewriteEngine On
  RewriteRule ^/command/?(.*)$ /torrent/command/$1 [P]

  ## The new location for WebUI. 127.0.0.1:9000 is where my 
  ## WebUI resides.  Change these details to match your own needs
  <Location /torrent/>
        ProxyPass http://127.0.0.1:9000/
        ProxyPassReverse http://127.0.0.1:9000/
  </Location>

```


The same will work for Utorrent with some slight mods:
```

  ProxyRequests off
  <Proxy *>
      allow from all
  </Proxy>

  RewriteEngine On
  RewriteRule ^/gui/?(.*)$ /torrent/gui/$1 [P]
  <Location /torrent/>
        ProxyPass http://127.0.0.1:9000/gui/
        ProxyPassReverse http://127.0.0.1:9000/gui/
  </Location>

```


Restart apache and you should be able to access WebUI through [http://yourlocalwebserver/torrent/](http://yourlocalwebserver/torrent/)


** Additional notes:  

I use a small self written portal to control access to my intranets webserver and I have been experimenting with some access control methods. 


This is what I have so far...  Requests to /torrent/ are only allowed if referred from the portal home page and if the Request is successful I add the correct Authorization header so that entering user/pass is not needed.

Again commented for clarity
```
 
ProxyRequests off
<Proxy *>
    allow from all
</Proxy>

###  Rewrite all requests not being referred from /portal/home.php
### back to the portal login page. I abit this is all abit hackish
RewriteEngine On
RewriteCond %{THE_REQUEST} "GET /torrent/ HTTP/1.1"  [NC]
RewriteCond %{HTTP_REFERER} !^(.*)/portal/home.php [NC]
RewriteRule ^.*$ /index.php [R=301,L]

RewriteRule ^/command/?(.*)$ /torrent/command/$1 [P]
<Location /torrent/>
  ##  Add the Auth header.  My details have been scrambled.  To get a
  ## header thats correct for your setup use the following:
  ## curl -v --digest -u youruser http://127.0.0.1:9000/ |grep Auth
  ##
  ## uri=%{REQUEST_URI}e to supply the header with the correct Request URL
  ## every time a document is requested.
  RequestHeader add Authorization "Digest username=\"user\", realm=\"Web UI Access\", nonce=\"XXXX\", uri=%{REQUEST_URI}e cnonce=\"XXX\", nc=XXX, qop=\"auth\", response=\"XXX\", opaque=\"XXX\", algorithm=\"MD5\""
  ProxyPass http://127.0.0.1:9000/
  ProxyPassReverse http://127.0.0.1:9000/
</Location>


```


That should get you pointed in a working direction :)  Hope this helps
-onemyndseye

---

### Post by onemyndseye on 2010-10-09
After further testing adding the digest header is not very reliable but it was worth a shot ;)  perhaps I am doing something wrong *shrug*

---


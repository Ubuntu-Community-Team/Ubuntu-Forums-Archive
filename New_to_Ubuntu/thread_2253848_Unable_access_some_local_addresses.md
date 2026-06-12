---
title: "Unable access some local addresses"
date: 2014-11-22
forum: New to Ubuntu
---

### Post by jashale on 2014-11-22
I want to use "dwww" content locally via this address: [http://jhnlt001/dwww/menu/](http://jhnlt001/dwww/menu/)

Also, I am unable to access this local site as well: [http://jhnlt001:8080/server/index.html](http://jhnlt001:8080/server/index.html)

I don't know what's wrong and have wasted several hours trying to troubleshoot this problem via both searching and trying various things.  How do I fix or troubleshoot this?

---

### Post by jashale on 2014-11-24
I fixed the problem by enabling cgi on the apache2 server.

sudo a2enmod cgi
sudo service apache2 restart

---


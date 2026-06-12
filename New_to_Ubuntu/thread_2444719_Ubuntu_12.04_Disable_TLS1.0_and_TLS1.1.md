---
title: "Ubuntu 12.04 Disable TLS1.0 and TLS1.1"
date: 2020-06-03
forum: New to Ubuntu
---

### Post by chrizty-0 on 2020-06-03
Hi Guys, I know this version of Ubuntu is end of life but is there anyway to disable TLS1.0 and TLS1.1?

Ubuntu 12.04.2 LTS
OpenSSL 1.1.0f
Apache/2.2.22 (Ubuntu)

When I try to modify the ssl.conf file with -all +TLSv1.2 
Then restart Apache2, I get an illegal command '+TLSv1.2'

Is it possible to disable TLS on this system without having to upgrade?

Thanks
Chris

---

### Post by dino99 on 2020-06-03
read this [https://askubuntu.com/questions/1117311/how-to-disable-tls-1-0-tls-1-1-on-apache](https://askubuntu.com/questions/1117311/how-to-disable-tls-1-0-tls-1-1-on-apache)
and/or this [https://www.digitalocean.com/community/questions/disable-old-tls-versions-1-0-1-1-for-apache-nginx-on-ubuntu-18-04-or-centos-7](https://www.digitalocean.com/community/questions/disable-old-tls-versions-1-0-1-1-for-apache-nginx-on-ubuntu-18-04-or-centos-7)

---

### Post by chrizty-0 on 2020-06-10
Hey Guys,
I have a Ubuntu 12.04 that has Apache2 2.22 installed and I am trying to upgrade to Apache2 2.23
I know these are old versions, however this Ubuntu is running an old web application that I use and I am looking to upgrade Apache to 2.23 to see if it will allow me to disable TLS1.0 and TLS1.1.

I have downloaded the httpd2.2.23 tar.gz and extracted it, ran the ./configure, make, make install
But, when I test which apache version is running it always comes back with Apache2.2.22.

Does Apache normally install over the top of the older version or am I missing something?

Thanks

---

### Post by coffeecat on 2020-06-10
@chrizty-0, I've merged your two threads. Please do not post duplicates. If you wish to bring a thread up to the top, simply bump it, rather than starting a new one.

---

### Post by Holger_Gehrke on 2020-06-10
Software compiled and installed from source usually installs into subdirectories of /usr/local/ while software installed from packages through apt or dpkg go into subdirectories of /usr/. So you probably have two binaries for apache (in /usr/sbin and /usr/local/sbin I think) and it depends on the start-up scripts in /etc/init.d (IIRC, 12.04 used the old init system and I haven't used that in a while) and possibly the order of directories in $PATH which one gets started.

Holger

---

### Post by ActionParsnip on 2020-06-10
I suggest you upgrade to a supported release of Ubuntu. Ubuntu 12.04 is EOL (End of life)

---

### Post by TheFu on 2020-06-10
There is another solution for the SSL issue.  Bring up a new 20.04 system, load nginx and have it be the reverse-proxy for your deprecated 12.04 system.  Let the current nginx handle the SSL, the certs, micro-caching, etc, but pass the requests to the old 12.04 system running without any SSL.  You'll want to lock down the 12.04 system to prevent any HTTP/HTTPS access from anywhere except the new 20.04 system.

And ... get off 12.04 ASAP.  You are 3 yrs late!  If you're paying Canonical for ESM support, you can contact them for help.  [https://ubuntu.com/esm](https://ubuntu.com/esm)

My understanding for these forums is that we should avoid posting EOL stuff, unless that is to get you migrated (some way) to a currently supported release.  Today, that would be 20.04 Server and if that fails, 18.04 Server.  Servers like yours need to stay on LTS while those are supported.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) has a chart for free support and paid, extended support.

---


---
title: "Install PHP &amp; MySQL on Ubuntu"
date: 2008-08-30
forum: Programming Talk
---

### Post by dodgingspam on 2008-08-30
I'd like to install PHP & MySQL to do some work offline. Is there a proven way to do on Ubuntu?

Thanks.

---

### Post by gmxgeek on 2008-08-30
install the packages from repos, which will run everything you need locally. No need for internet at all, except to get package :P

[http://localhost](http://localhost)

When all is set up

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

should help

---

### Post by Kadrus on 2008-08-30
[LAMP(Linux Apache mySQL PHP) Installation Under Ubuntu.]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop")

---

### Post by jespdj on 2008-08-30
The preferred way to install software on Ubuntu is via the package management system (Synaptic or apt-get).
```
sudo apt-get install mysql-server mysql-client php5
```

---

### Post by dodgingspam on 2008-09-01
OK, I was able to find PHP and MySQL following documentation from the link posted by Kadrus (Thanks!) However, when I get to "Adding a virtual host to your LAMP server" and try to restart the server at the end I get errors:

> svs@svs-laptop:/etc/apache2$   sudo nano /etc/hosts
sudo: unable to resolve host svs-laptop
svs@svs-laptop:/etc/apache2$ sudo /etc/init.d/apache2 restart
sudo: unable to resolve host svs-laptop
 * Restarting web server apache2                                                apache2: apr_sockaddr_info_get() failed for svs-laptop
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Mon Sep 01 23:48:06 2008] [warn] NameVirtualHost 127.0.1.1:80 has no VirtualHosts
[Mon Sep 01 23:48:06 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
apache2: apr_sockaddr_info_get() failed for svs-laptop
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Mon Sep 01 23:48:16 2008] [warn] NameVirtualHost 127.0.1.1:80 has no VirtualHosts
[Mon Sep 01 23:48:16 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                         [ OK ]
svs@svs-laptop:/etc/apache2$ 


Bit at a loss....

---

### Post by -grubby on 2008-09-02
I use [Xampp](http://php.8ez.com/drsmall/blog/?p=96), it's pretty convienent, but **NOT** for use other than local testing, as it's very insecure, but convienent

---

### Post by mssever on 2008-09-02
Why not just do a ```
sudo tasksel
```and get everything you need? IMO, XAMPP is reasonable on Windows since that OS doesn't have decent package management. But in Ubuntu, it only adds a layer of complexity. Just use the standard packages from the repos, forget [LX]AMPP exists, and you're good to go.

---

### Post by OffAxis on 2008-09-02
Can you post your
**/etc/hosts**

and 
**/etc/apache2/httpd.conf** (if that's where you added it)
files?

---

### Post by dodgingspam on 2008-09-10
/etc/hosts
> 
127.0.0.1 localhost
127.0.1.1 mydomaincom

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


/etc/apache2/httpd.conf 
> 
<VirtualHost *>
     ServerName mydomaincom
     DocumentRoot /home/user/Projects/SC/public_html
 </Virtualhost>


---


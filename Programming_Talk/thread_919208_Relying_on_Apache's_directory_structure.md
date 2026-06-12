---
title: "Relying on Apache's directory structure?"
date: 2008-09-13
forum: Programming Talk
---

### Post by Znupi on 2008-09-13
Hi, I'm building an Apache Administrator (or at least that's what I call it) in Python and GTK (and Glade). It's coming along pretty nicely (it's my first Python application), it sits in the system tray and reports whether Apache is active or not. It can also start/stop/restart/graceful apache (if run as root).

Anyway, the idea is that I'm relying on Apache's directory structure. On my system I compiled Apache myself with the default --prefix of /usr/local/apache2. The program has a configuration file in which this prefix used when compiling is specified. Then it basically checks if there's a <prefix>/logs/httpd.pid file (and also a /proc/<pid> directory) to report whether Apache is running or not. It also runs <prefix>/bin/apachectl -k start|stop|restart|graceful when the user clicks on the respective buttons.

The question is, is it a safe way to rely on Apache's directory structure? Or does it change depending on how you install it? E.g. if you sudo apt-get install apache2, does it keep this structure? What's the <prefix> then?

Thanks!

---

### Post by drubin on 2008-09-13
I dont think you can. Because  you could install xmapp, which by default installs /opt/.

---

### Post by drubin on 2008-09-13
You could take a look how [webmin]("http://www.webmin.com/")  does it? :)

---

### Post by Znupi on 2008-09-13
> **rubinboy said:**
> I dont think you can. Because  you could install xmapp, which by default installs /opt/.
I actually use XAMPP on my server. So what if it installs to /opt? I can simply configure my application (it has a .conf file) to use /opt/lampp as the <prefix>. After that, it can find the httpd.pid file in /opt/lampp/logs/httpd.pid and the apachectl binary in /opt/lampp/bin/apachectl.
And I don't really feel like diving into webmin's source knowing that my way could actually be the right one.

---

### Post by drubin on 2008-09-13
Using XAMPP on your server could be a security flaw. Reading the readme states this is for development and testing and should not be used on production servers....

But Ye you can trust the dir structoure of appache. at least the /etc/apache2/* 

although on other distro's such as Fedora/CentOS it is 
/etc/httpd/*

---

### Post by Znupi on 2008-09-13
Actually I just found apachectl -V which seems very helpful for what I'm trying to do. I think I should rely on that. But what's the best way of finding the apachectl binary? I'm thinking it like this: search for in in the paths specified by the PATH env, search for it in /usr/local/apache2/bin (maybe the user compile Apache themselves, but didn't add the folder to PATH) and also check /opt/lampp/bin , maybe the user is using XAMPP. Souds like a plan?

---

### Post by Znupi on 2008-09-13
> **rubinboy said:**
> Using XAMPP on your server could be a security flaw. Reading the readme states this is for development and testing and should not be used on production servers....
I know, it's not a big server, it just hosts one site and a few testing sites (not public), plus I passworded everything.
> **rubinboy said:**
> But Ye you can trust the dir structoure of appache. at least the /etc/apache2/*

although on other distro's such as Fedora/CentOS it is 
/etc/httpd/*
I guess I should check those folders out, too, thanks :)

---


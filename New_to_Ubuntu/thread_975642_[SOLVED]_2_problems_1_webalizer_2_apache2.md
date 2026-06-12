---
title: "[SOLVED] 2 problems 1 webalizer 2 apache2"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by niiklas on 2008-11-08
Hello.

1:
I installed webalizer a few days ago, i made it update once each hour. But i don't get any new data since november 2 every day after that is empty. What have i done wrong? it does update each hour Generated 08-Nov-2008 21:00 CET but doesn't give any new data.
example: [http://img98.imageshack.us/my.php?image=123eu9.jpg](http://img98.imageshack.us/my.php?image=123eu9.jpg)

2:
My apache2 server is running okey and so but today i noticed a error message when trying to restart it:

```

niklas@ubuntu:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2 
 apache2: Could not reliably determine the server's fully qualified domain name,
using 127.0.1.1 for ServerName
[Sat Nov 08 21:46:42 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting apache2: Could not reliably determine the server's fully qualified                                                 
 domain name, using 127.0.1.1 for ServerName
[Sat Nov 08 21:46:43 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
 [ OK ]

```

The server still works good but i get this error each time i start/stop/restart it. It has not been like this before started today.

---

### Post by niiklas on 2008-11-08
bump

---

### Post by hictio on 2008-11-08
#1-
After you installed Webalizer, did it worked, or for a few days, or stoped working ever since you installed it?


#2-
Does you box have a FQDN (Fully qualified domain name) assigned? That is, a hostname that is properly registered on some DNS?
Probably not, that's why the error.

---

### Post by niiklas on 2008-11-08
> **hictio said:**
> #1-
After you installed Webalizer, did it worked, or for a few days, or stoped working ever since you installed it?


#2-
Does you box have a FQDN (Fully qualified domain name) assigned? That is, a hostname that is properly registered on some DNS?
Probably not, that's why the error.

im not 100% sure if it was working after i installed webalizer but i got some statistics from october and 2 days of november.

---

### Post by hictio on 2008-11-08
> **niiklas said:**
> im not 100% sure if it was working after i installed webalizer but i got some statistics from october and 2 days of november.

I have never seeing a Webalizer setup to graph data every hour, all I have seeing dump the data once a day.
Can you post the config file? Check '/etc/webalizer.conf'.


> **niiklas said:**
> 
I got server.tobbeno1.se pointing to my server. I need to enter that somewhere in the configs?

What I mean is this:
Open a Terminal and type 'hostname'.
Does the hostname that returns the hostname command (doh!) have a valid IP address registered on a DNS server somewhere?

---

### Post by niiklas on 2008-11-08
l

---

### Post by hictio on 2008-11-08
Thanks, there is something I don't understand from the config.

```

LogFile /var/log/apache2/access.log.1

```

This is telling Webalizer to read the hits information not from the running Apache log, but from the rotated one.
Mine, not on a Ubuntu box, tho, points to the actual log:
```

LogFile /var/log/httpd/ssl_access_log

```

The actual path is just an example.

How did you set Webalizer to graph the data every hour, thru a cronjob? Did you run that cronjob manually to see if it reports any error? The same goes for the webalizer, something like this:
```

webalizer -c /etc/webalizer.conf -d /var/log/httpd/ssl_access_log

```


> 
niklas@ubuntu:/etc/webalizer$ hostname
ubuntu

i don't have that registred on some dns server.~:S


That's why Apache complains upon starting.

---

### Post by niiklas on 2008-11-08
i didn't change any defaults in webalizer.conf before. changed ```
LogFile /var/log/apache2/access.log.1
```
to
```
LogFile /var/log/apache2/access.log
```

and now it works perfect.

And for the second problem where can i register the dns~ so i won't get ther error?

one.com currently handles my dns and such~.

---

### Post by pgorillaman on 2008-11-08
In your apache2.conf, add the following line:

ServerName server.tobbeno1.se:80

---

### Post by niiklas on 2008-11-08
> **pgorillaman said:**
> In your apache2.conf, add the following line:

ServerName server.tobbeno1.se:80

i did that and now i only get these errors:

```

root@ubuntu:/etc/apache2# /etc/init.d/apache2 restart
 * Restarting web server apache2
[Sun Nov 09 00:35:18 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Sun Nov 09 00:35:19 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
[ OK ]

```

---

### Post by hictio on 2008-11-08
Was the "ServerName" entry on your httpd.conf commented to begin with?

---

### Post by pgorillaman on 2008-11-08
You probably have virtual host declared twice

---

### Post by niiklas on 2008-11-08
g

---

### Post by pgorillaman on 2008-11-08
Ubuntu uses apache2.conf instead of httpd.conf. If NameVirtualHost * is in apache2.conf as well as this site file, when they get combined together they will give you that error. You only need one declaration.

---

### Post by niiklas on 2008-11-08
n

---

### Post by niiklas on 2008-11-08
solved

---


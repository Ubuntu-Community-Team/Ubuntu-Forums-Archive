---
title: "apahce server"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by inter-m on 2008-11-26
im trying to learn PHP... and already installed apache2 to my laptop... thing is my course im taking is on windows... i was instructed to save a PHP file to htdocs... im really lost i dont know where to find that file... thanx in advance...

K.H.

---

### Post by kestrel1 on 2008-11-26
htdocs is a folder & I think the default location is /usr/local/apache/share/htdocs/
This is the folder where you should be saving your website files too, hence that is why you are told to save the PHP file there.
Another way around this is to find a webhost that has PHP enabled & use the space there to save your files for testing over the internet.

---

### Post by NullHead on 2008-11-26
I thought it was it /var/www/

---

### Post by kestrel1 on 2008-11-26
I supose it really depends on how it was installed.

---

### Post by inter-m on 2008-11-27
> **kestrel1 said:**
> htdocs is a folder & I think the default location is /usr/local/apache/share/htdocs/
This is the folder where you should be saving your website files too, hence that is why you are told to save the PHP file there.
Another way around this is to find a webhost that has PHP enabled & use the space there to save your files for testing over the internet.

doing it on a webhost  is a nice quick fix in my case... and i have thought about it... but i really want to understand how to setup and manage an apache server on ubuntu...

as for the default location u gave me does not exist... but /var/www/ does... and when i saved a PHP file and tried to call it on my browser by typing [http://localhost/firstcode.php](http://localhost/firstcode.php) it returned with a msg saying that the file does not exist...

---

### Post by Kareeser on 2008-11-27
Gr. Apache on windows is slightly different on Linux, it's similar to taking a course with a previous edition of the textbooks... some config files are in different areas, and some options aren't even enabled...

In my experience, VirtualHosts were off by default on Windows, but enabled on Unix. However, it could've been a version difference. Who knows.

In your config file (/etc/apache2/apache2.conf OR /etc/apache2/sites-available/default), what is the "DocumentRoot"?

---

### Post by kestrel1 on 2008-11-27
Have you started the apache server?
To start it under Linux use this command:
```
./apachect1 start
```
Also your configuration file httpd.conf needs to be set for your server & the port that it should listen on (normally port 80)
If you are using a stand alone machine set the server name to 127.0.0.1 (the loopback address)
A good book for learning about PHP, MySQL & Apache is Sams teach yourself PHP, MySQL & Apache in 24 hours:
[http://www.amazon.co.uk/Sams-Teach-Yourself-MySQL-Apache/dp/067232976X/ref=sr_1_1?ie=UTF8&s=books&qid=1227808931&sr=8-1](http://www.amazon.co.uk/Sams-Teach-Yourself-MySQL-Apache/dp/067232976X/ref=sr_1_1?ie=UTF8&s=books&qid=1227808931&sr=8-1)

---


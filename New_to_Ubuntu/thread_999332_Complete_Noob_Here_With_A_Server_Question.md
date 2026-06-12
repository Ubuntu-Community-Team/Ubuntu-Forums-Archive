---
title: "Complete Noob Here With A Server Question"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by kyle99 on 2008-12-01
Ok, I have installed a the Ubuntu 8.10 desktop edition. I'm am thinking about running a website server from my computer. Is there any way I can do this from my computer? Or do I have to install the server edition?

Thanks a ton.

~Kyle

---

### Post by halitech on 2008-12-01
you can do it from a workstation install

open a terminal and paste this in
```
sudo apt-get install apache2
```
technically all  you need but if you want to get fnacy, look into installing php, MySQL, tomcat and phpmyadmin.

---

### Post by kyle99 on 2008-12-01
Ok, thanks for that. I did that, and got this:
apache2 is already the newest version.

I already have LAMP installed. What do I do to put these onto the web? 

Thanks a ton, I appreciate the help.

---

### Post by halitech on 2008-12-01
are  you behind a router? do you have a static IP address?

easiest was I've found is to sign up for a free dynamic hostname at dyndns.com or no-ip.com and run the clients to keep your ip address current. if you have a router, you'll need to forward port 80 from the router to the server computer.

---

### Post by kyle99 on 2008-12-01
I signed up at DynDNS.com, and I do have a domain with the 2 nameservers. What do I do next? 

Thanks :)

Kyle

---

### Post by halitech on 2008-12-01
are you planning on hosting an actual domain on your system?

---

### Post by kyle99 on 2008-12-01
Well, what I am planning to do is just host a couple files on my system, and want them to be accessed from a computer anywhere.

---

### Post by halitech on 2008-12-01
ok then you don't really need an actual domain, just use the free account name you signed up for at dyndns. next step would be configuring your router to forward port 80 to your computer.

---

### Post by kyle99 on 2008-12-01
Ok, I'm using a Wireless USB adapter, but I do have a router, how would I go about doing this? Thanks!

~Kyle

---

### Post by halitech on 2008-12-01
wireless is not the best connection to use for a server but if thats all you have, then we'll have to work with it.

what kind of router do you have?

[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

check this out for info. Heading out and don't want to leave you hanging :)

---

### Post by kyle99 on 2008-12-01
I have this router:

[http://portforward.com/english/routers/port_forwarding/Netgear/WNR834B/WNR834Bindex.htm](http://portforward.com/english/routers/port_forwarding/Netgear/WNR834B/WNR834Bindex.htm)

---

### Post by kyle99 on 2008-12-01
Darn, didn't see the second page and thought that I didn't post that yet. Sorry.

---

### Post by halitech on 2008-12-02
ok, so follow the instructions here:

[http://portforward.com/english/routers/port_forwarding/Netgear/WNR834B/Apache.htm](http://portforward.com/english/routers/port_forwarding/Netgear/WNR834B/Apache.htm)

---

### Post by kyle99 on 2008-12-02
Ok, I'm good until I foward the second port. I already have a port 443 called Slingbox. Can apache use something else besides 443, or am I screwed?

---

### Post by halitech on 2008-12-02
you only need port 443 forwarded if you are using https connections (which usually won't work on a home system)

---

### Post by kyle99 on 2008-12-02
Ok, so it's all fowarded, how do I access my site?

---

### Post by halitech on 2008-12-02
depending on your router, [http://localhost](http://localhost) may be the only way. Some routers will not loop back properly. For others, give them the address you set up.

---

### Post by kyle99 on 2008-12-02
Thanks a ton for your help, got it working :)

---

### Post by halitech on 2008-12-02
glad to hear its working for you :) mark the thread as solved so others will know.

---

### Post by GROMS on 2008-12-03
> **halitech said:**
> you can do it from a workstation install

open a terminal and paste this in
```
sudo apt-get install apache2
```
technically all  you need but if you want to get fnacy, look into installing php, MySQL, tomcat and phpmyadmin.

You lost me. I did the ```
sudo apt-get install apache2 php5
``` and there was an install. also got the apache2-doc installed. Opened the browser for the url 127.1.1.1 and it opened a "it works" page. BUT I can't seem to get any other page to work.
 
First, how do I get to the manuel?
Second, how do I get stuff in user/www/webpage.{html, php, etc}?
Third, how do I get to the server to make changes?
Forth, could not find phpmyadmin and there are umteen files for MySQL, 3 for tomcat, a big fist full for Python and Ruby. What ones do you get through Synaptic??

Last but not least (for this knowledge challenged)how do I make this all work on Hardy desktop. What I want to do is write code and test locally before uploading to websites.

All the help you can spare is greatly appreciated.
Stephen

---

### Post by halitech on 2008-12-04
might be better to open a new thread since this one is closed :)

1. for the manual, open a terminal and type```
man apache2
```

2. the default location is /var/www (owned by root so you can't just copy stuff in there). you can modify /etc/apache2/apache2.conf file to point to another location if you want to have it in your home folder.

3. us gksu nautilus to open a root file browser and copy files into /var/www

4. see here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) for info on installing and setting up beyond apache

---


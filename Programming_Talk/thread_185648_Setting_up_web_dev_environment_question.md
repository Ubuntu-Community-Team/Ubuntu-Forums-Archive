---
title: "Setting up web dev environment question"
date: 2006-06-01
forum: Programming Talk
---

### Post by Bunkai on 2006-06-01
I recently installed Breezy with the aim of setting up a LAMP web dev environment.

Can anyone who has done this tell me:

1. Should I install in this order MySQL -> Apache -> PHP?

2. Any configuration/setup pitfalls to be avoided?

Thanks.

---

### Post by elemental666 on 2006-06-02
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html) - enjoy!:D

---

### Post by David Marrs on 2006-06-03
it's quite easy, really. Just install the php apache module, the mysql server and the php-mysql interface. I don't think there's anything more to it than that. You'll also want a mysql client. mysql-query-browser is a nice gui app. You could also install php-cli which is useful for debugging (text editors and IDEs  use it to debug scripts, for example). 
```
sudo apt-get install libapache2-mod-php5 mysql-server php5-mysql mysql-client-5.0
```
Sites get stored in /var/www/

---

### Post by Bunkai on 2006-06-06
Thanks.

One thing to note for those who are browsing this bacause they are interested in it: PHP5 doesn't yet work with Apache2 in threaded mode (worker) so use the mpm-prefork package. I have to go back and install that.

---


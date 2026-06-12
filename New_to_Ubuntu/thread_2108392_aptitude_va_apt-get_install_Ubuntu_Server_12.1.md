---
title: "aptitude va apt-get install Ubuntu Server 12.1?"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by jmill134 on 2013-01-24
I'm building a linux server right now and will be running the following commands. I am wondering if I should use apt-get install instead and what the difference is?

aptitude update
aptitude upgrade
aptitude install apache2 php5 libapache2-mod-php5 php5-imap
aptitude install mysql-server mysql-client php5-mysql
aptitude install phpmyadmin

Thanks in advance!?

---

### Post by prodigy_ on 2013-01-24
**apt-get** is more common and you really just need to substitute it for **aptitude** here. Also depending on what you need that server for you might want to use 12.04 instead. LTS releases (like 12.04) are supported for much longer (5 years for server versions).

---

### Post by jonobr on 2013-01-24
There are  tonnes of posts on this all over the place
Like

[here]("http://unix.stackexchange.com/questions/767/what-is-the-real-difference-between-apt-get-and-aptitude-how-about-wajig/935#935") or
[Here]("http://askubuntu.com/questions/1743/is-aptitude-still-considered-superior-to-apt-get")
or
[here]("http://askubuntu.com/questions/1743/is-aptitude-still-considered-superior-to-apt-get/1749#1749")

I would read and figure which ever one works for you

warm regards

---


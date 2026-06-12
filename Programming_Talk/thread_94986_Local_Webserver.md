---
title: "Local Webserver"
date: 2005-11-25
forum: Programming Talk
---

### Post by dwessell on 2005-11-25
Hi all.. In windows I used a few pre-built programs to automatically setup a webserver (Apache, PHP, MySQL, etc..) on a local machine for testing purposes.. Is there such a thing for linux/ubuntu for easy standard setups?

Thanks
David

---

### Post by Corvillus on 2005-11-25
Yeah, you can set up a LAMP stack in Ubuntu quite easily
```

sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install mysql-server
sudo apt-get install libapache2-mod-auth-mysql
sudo apt-get install php5-mysql

```

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---


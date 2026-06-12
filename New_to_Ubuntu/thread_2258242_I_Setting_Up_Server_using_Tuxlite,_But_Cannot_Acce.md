---
title: "I Setting Up Server using Tuxlite, But Cannot Access dbgui"
date: 2014-12-26
forum: New to Ubuntu
---

### Post by uolover on 2014-12-26
Hi, I am newbie, I have setting up a vps server with tuxlite. After the installation, I believed mysql and phpmyadmin already installed, dbgui also sets on. But when I try to browse into dbgui, [http://mydomain.com/dbgui](http://mydomain.com/dbgui), it shows Internal Server Error screen.

Please help me to make this dbgui work, thanks :)

---

### Post by uolover on 2014-12-26
got it, it's permissions problems, tuxlite is outdated :(

```
chown www-data:www-data /var/run/php5-fpm*
```

---


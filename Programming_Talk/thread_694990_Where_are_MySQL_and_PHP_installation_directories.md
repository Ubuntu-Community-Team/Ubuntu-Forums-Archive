---
title: "Where are MySQL and PHP installation directories?"
date: 2008-02-12
forum: Programming Talk
---

### Post by standerby on 2008-02-12
I had installed MysQL and PHP 5 using apt-get. When I try to compile SQL relay it needs mysql-prefix and php-prefix. Where can I find these information? Thanks.

---

### Post by lnostdal on 2008-02-13
hi there,
try this:

```

dpkg -L mysql-server-5.0
dpkg -L php5-common
dpkg -L libapache2-mod-php5

```

..etc. =)

---


---
title: "Redirect all output from command"
date: 2015-06-09
forum: New to Ubuntu
---

### Post by CrewDK on 2015-06-09
Is there any way to redirect REALY all output from something like that?

```
apt-get install -y php5 php5-mysql libapache2-mod-php5 php5-memcache php5-imagick php5-recode php5-mcrypt php5-imap memcached php5-curl 2>&1 > /dev/null
```

As you can see i already tryed redirect anything to /dev/null but anyway I can still see setup process in my console :(   

```
150609 16:46:39 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
150609 16:46:39 [Note] /usr/sbin/mysqld (mysqld 5.5.43-0ubuntu0.14.04.1) starting as process 2492 ...
mysql start/running, process 2624
php5_invoke: Enable module json for apache2 SAPI
php5_invoke: Enable module json for cli SAPI

Creating config file /etc/php5/mods-available/pdo.ini with new version
php5_invoke: Enable module pdo for apache2 SAPI
php5_invoke: Enable module pdo for cli SAPI

.....


php5_invoke: Enable module imagick for cli SAPI
&#1044;&#1083;&#1103; &#1087;&#1088;&#1086;&#1076;&#1086;&#1083;&#1078;&#1077;&#1085;&#1080;&#1103; &#1085;&#1072;&#1078;&#1084;&#1080;&#1090;&#1077; &#1083;&#1102;&#1073;&#1091;&#1102; &#1082;&#1083;&#1072;&#1074;&#1080;&#1096;&#1091;...
```


Maybe i missed something?

---

### Post by Lars Noodén on 2015-06-09
```
foo > /dev/null 2>&1
```

The order matters in this case.  You have to first redirect stdout then tell stderr to go there too.

---

### Post by CrewDK on 2015-06-10
Oh, thnx. Didn't know that.

---


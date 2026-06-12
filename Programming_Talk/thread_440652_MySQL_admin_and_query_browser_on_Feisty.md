---
title: "MySQL admin and query browser on Feisty"
date: 2007-05-11
forum: Programming Talk
---

### Post by pan69 on 2007-05-11
Hi guys,

I've basically a clean Feisy installation. My machine is going to be a developer box so I;ve already installed Eclipse (WTP), Tomcat5.5, Apache2 and MySQL.

Now, to do some table editing and database admin stuff (like making backups etc.) I want to install the MySQL GUI tools. Besides the fact that they only seem to run from the /opt folder (:confused:) I get the following message when starting the MySQL administrator from the command line:

> /usr/share/themes/Glossy/gtk-2.0/gtkrc:35: error: unexpected character `@', expected string constant
Fontconfig warning: line 32: unknown element "cachedir"
Fontconfig warning: line 33: unknown element "cachedir"
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 18: invalid match target "scan"
./mysql-administrator-bin: symbol lookup error: /usr/lib/libbonoboui-2.so.0: undefined symbol: g_type_register_static_simple


Anyone an idea what to do with this one?

Thanks!

---

### Post by cknoblock on 2007-05-12
Hello,

I think this is a known, open bug with mysql and feisty:

[http://bugs.mysql.com/bug.php?id=27365](http://bugs.mysql.com/bug.php?id=27365)

-c

---

### Post by t0mc4t on 2007-06-13
I do have the same problem here..
Does it mean we can't use the mysql admin in Feisty at this moment?
Thanks...

---

### Post by PartickThistle on 2007-06-13
Why not use the Quantum DB plug-in for Eclipse? 

Also, are you using the MySQL Query Browser/Administrator from the repos or from mysql.com?   I'm using the repos version and it works without a hitch.

---

### Post by t0mc4t on 2007-06-14
Hi... I'm using MySQL admin from mysql.com
Any idea how to fix this?
Thx..

---


---
title: "can't create a directory in /run (/var/run)"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by knighth001 on 2012-06-29
I'm trying to get tomcat to start on boot. I have a startup script in /etc/init.d that attempts to start tomcat as user www-data. the problem is that it tries to create a pid file under /var/run aka /run. But www-data can't write to /run.  So I tried to create a directory or a file under /run as root and then chown it to www-data and then run the init.d script. and it works.   My problem is that whenever I restart the machine. the directory or files I create under /run aren't there anymore. they disappear. and I have to go through the process of recreating them every time I boot.  Help...how can I get a persistent directory under /run?

---


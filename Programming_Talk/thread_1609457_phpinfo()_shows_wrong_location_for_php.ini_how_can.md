---
title: "phpinfo() shows wrong location for php.ini how can I revert it back?"
date: 2010-10-30
forum: Programming Talk
---

### Post by ndefontenay on 2010-10-30
Hi,

my phpinfo();
looks like this:

```
Configuration File (php.ini) Path 	/usr/local/zend/etc 
Loaded Configuration File 	/tmp/zend_debug/session2680066595081096399.tmp/php.ini
Scan this dir for additional .ini files 	/usr/local/zend/gui/lighttpd/etc/conf.d 
```

I tried installing the zend framework through the repository but then decided to switch to a manual installation. I got my zend framework installed at /opt/ZendFramework, using this tutorial:

[http://www.howtoforge.com/basic-web-server-on-ubuntu-9.04-with-zend-framework]("http://www.howtoforge.com/basic-web-server-on-ubuntu-9.04-with-zend-framework")

The configuration over all seems alright except for php. I did modify /etc/php5/php.ini but it looks like php is looking somewhere else, in a place which in fact does not exist...

Any help would be welcome

thanks

Nico

---

### Post by ndefontenay on 2010-11-04
At the end of the day when things gets too messy only a good old apt-get remove php5* could help.

Solved.

---


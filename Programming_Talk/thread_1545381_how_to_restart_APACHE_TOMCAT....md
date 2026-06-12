---
title: "how to restart APACHE TOMCAT..."
date: 2010-08-03
forum: Programming Talk
---

### Post by OnlineBuddy on 2010-08-03
i have tomcat which is downloaded from repos and is working fine..
.
.but it starts automatically as (JSVC) process....
.
i want to know if there is a shell script for **SHUTDOWN **and **STARTUP, **so thati could control when it runs..!!
.

---

### Post by Some Penguin on 2010-08-04
Check /etc/init.d for the tomcat6 script, and /etc/rc#d (replace # with the appropriate runlevel)

---

### Post by phrostbyte on 2010-08-05
service tomcat6 stop
service tomcat6 start

---


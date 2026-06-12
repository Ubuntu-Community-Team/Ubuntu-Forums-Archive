---
title: "Problem installing Apache"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by mancroft on 2008-05-25
I am trying to install Apache with sudo apt-get install apache2 and am getting the following error:

```
Module authn_file installed; run /etc/init.d/apache2 force-reload to enable.
Module authz_host installed; run /etc/init.d/apache2 force-reload to enable.

Setting up apache2-mpm-worker (2.2.8-1ubuntu0.1) ...
 * Starting web server apache2
apache2: Syntax error on line 295 of /etc/apache2/apache2.conf: 
Could not open configuration file /etc/apache2/conf.d/zoneminder.conf: 
No such file or directory
[fail]
invoke-rc.d: initscript apache2, action "start" failed.

```

Any ideas, please?

---

### Post by hyper_ch on 2008-05-25
remove the zoneminder.conf from the apache2.conf

---

### Post by mancroft on 2008-05-25
Bingo, hyper_ch!

---

### Post by hyper_ch on 2008-05-25
reading the error messages normally help....  the usually contain a lot of information.

---

### Post by saj0577 on 2008-05-25
Rather then remove it if i was you i would just comment it, but thats just my opinion.

Saj

---


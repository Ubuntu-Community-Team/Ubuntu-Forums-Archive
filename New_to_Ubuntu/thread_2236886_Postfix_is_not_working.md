---
title: "Postfix is not working"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by chandrasekhar3 on 2014-07-29
Hi,

    ----> sudo postfix status           [sudo] password for sekhar: 
           postfix/postfix-script: the Postfix mail system is running: PID: 3999    

   ------>   sudo postfix check              postfix/postfix-script: warning: not owned by root: /etc/postfix/sasl_passwd
              postfix/postfix-script: warning: not owned by root: /etc/postfix/sasl_passwd.db
              postfix/postfix-script: warning: group or other writable: /etc/postfix/./dynamicmaps.c f
              postfix/postfix-script: warning: group or other writable: /etc/postfix/./postfix-files
              postfix/postfix-script: warning: group or other writable: /etc/postfix/./post-install
              postfix/postfix-script: warning: group or other writable: /etc/postfix/./postfix-script
              postfix/postfix-script: warning: group or other writable: /etc/postfix/./main.cf
              postfix/postfix-script: warning: group or other writable: /etc/postfix/./master.cf

---

### Post by ubudog on 2014-07-29
Hi, try:
```
sudo chown -R root:root /etc/postfix/
```

This will change the ownership of the /etc/postfix directory to root.

---


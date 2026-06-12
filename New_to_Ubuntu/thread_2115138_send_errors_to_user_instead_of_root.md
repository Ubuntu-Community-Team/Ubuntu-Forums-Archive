---
title: "send errors to user instead of root"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by marchelloUA on 2013-02-12
Hi all, 

I've looked into /var/log/syslog and seen that some errors occured. As far as I know, errors go to root mailbox. How do I change settings in order to send errors into user mailbox instead of root ?

---

### Post by SeijiSensei on 2013-02-12
Errors are not automatically mailed anywhere; they are simply logged.

You can install [logwatch](https://help.ubuntu.com/community/Logwatch) which will scan the logs and send you an email.

---


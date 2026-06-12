---
title: "Allow pure-ftpd user to upload to /var/www/?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Faggotry on 2008-09-06
Hi, I use pure-ftpd on my server and after some trail&error I managed to add a user with the command "sudo pure-pw useradd jesus -u ftpuser -g ftpusers -d /var/www".
I can login and view /var/www/ with no problem but how do I change jesus access to /var/www/ so that he can upload files?
Can't find any chmod options for jesus.

---

### Post by ggaaron on 2008-09-06
Maybe 'cat /etc/pureftpd.passwd', uid and gid numbers for your user should be there. Or better 'pure-pw show jesus'.

[http://download.pureftpd.org/pub/pure-ftpd/doc/README.Virtual-Users](http://download.pureftpd.org/pub/pure-ftpd/doc/README.Virtual-Users)

---


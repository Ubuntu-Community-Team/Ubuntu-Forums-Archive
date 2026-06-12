---
title: "Help with users vsftpd"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by perksa on 2013-05-03
So I used [this guide]("http://www.sigerr.org/linux/setup-vsftpd-custom-multiple-directories-users-accounts-ubuntu-step-by-step") to setup vsftpd with multiple users locked into their own dir. The problem I am having is I make my users/pass and when I try to log on the server only some work and some get an error with invalid password. I read somewhere that it has to do with Apache2 and PAM conflicting (htpasswd generates MD5 hashes in the Apache format, which you can verify by seeing that they start with $apr1$, but PAM only supports formats that your platform's implementation of crypt(3)) but I can not figure out a way to make the passwords in a why that PAM will recognize. I would really appreciate any help. Thanks!

---

### Post by perksa on 2013-05-03
Shoot forgot to mention Ubuntu 12.04 if it matters.

---


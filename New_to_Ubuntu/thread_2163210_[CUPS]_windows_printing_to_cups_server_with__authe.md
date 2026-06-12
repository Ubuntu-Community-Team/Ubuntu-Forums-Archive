---
title: "[CUPS] windows printing to cups server with  authentication required"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by massonc on 2013-07-17
Hello,

To print from unix through ipp, the authentication is required (Basic authentication) . It's works.

Now I want to permit printing from windows with samba (domain authentication), but I have the following problem : samba don't give any credential to cups so cups refuse to print.

Do you know how we can make this?

I have tested some workaround but nothing is working for the moment.

Best regards

---

### Post by dino99 on 2013-07-17
samba seems affected by a bug ; workaround joined.
[http://askubuntu.com/questions/156863/configuring-samba-to-allow-use-of-cups-printer](http://askubuntu.com/questions/156863/configuring-samba-to-allow-use-of-cups-printer)

---


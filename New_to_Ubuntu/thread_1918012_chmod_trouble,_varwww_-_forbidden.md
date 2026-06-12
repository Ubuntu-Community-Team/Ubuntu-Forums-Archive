---
title: "chmod trouble, /var/www - forbidden"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by Woopers on 2012-01-31
Hey guys,

I've been trying to set up a webserver using Ubuntu. So far I've succeeded quite well, I have my vsFTPd, Apache2, Php5 and so on. It was all working quite well except for the FTP. I was told to change my chmod values on my /var/www/ to be able to upload files so that I could view them online - so I did. Now all of a sudden, I can upload files just fine, but I got a 403 when trying to access my webserver.

Help please!

---

### Post by cavh on 2012-01-31
Please post the output of 

```
stat /var/www
```

---


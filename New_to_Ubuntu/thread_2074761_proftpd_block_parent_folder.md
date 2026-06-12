---
title: "proftpd block parent folder"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by driekus77 on 2012-10-22
Hello,

I have a FTP share /var/ftp/folder1 but when i log in with the user i can access the root directory / 
i just only want to give him access to folder 1 and not more .
Can somebody help me . 
I use Ubuntu Server 12.04LTS with Webmin

Dirk

---

### Post by Wim Sturkenboom on 2012-10-22
I think [http://www.proftpd.org/docs/howto/Chroot.html](http://www.proftpd.org/docs/howto/Chroot.html) will help

No experience with proftpd (I'm using vsftpd).


PS What your looking for is a chroot jail so you can use that in your searches on the web.

---


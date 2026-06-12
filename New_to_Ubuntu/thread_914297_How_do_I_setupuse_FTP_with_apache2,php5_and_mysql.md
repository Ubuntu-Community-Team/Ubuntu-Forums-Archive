---
title: "How do I setup/use FTP with apache2,php5 and mysql?"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by NorthernPaladin on 2008-09-08
A quick question, I have apache2,php5 and mysql installed. What else do I need to allow my friend to upload files to the server which is hosting forum we put up with phpBB3? for example styles for it and like

---

### Post by mevets on 2008-09-08
in short,
```

sudo apt-get install proftpd

```
Thats a non-gui ftp server, for a gui version you might want to install gproftpd.

Have a look at [http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/](http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/)

---

### Post by NorthernPaladin on 2008-09-08
Installed it, but after some searching I´d like to ask if it is posible to give permission to the ftp program to write in var/www/phpBB3 dir?

---

### Post by Alex53 on 2008-09-16
I have the same problem. Setting up /var/www/ as the FTP root directory doesnt seem to be allowed. 

I want to have people being able to upload via ftp and then the file listings to be visible via http, for public/anonymous users to download.

---


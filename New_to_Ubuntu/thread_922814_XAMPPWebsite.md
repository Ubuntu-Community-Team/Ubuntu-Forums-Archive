---
title: "XAMPP/Website"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by SuperPetRalf on 2008-09-17
So I need an apache and PHP server, and I needed them like 5 minutes ago, I'm new to Linux and I tried installing XAMPP, like the documentation stated. One thing lead to another and I screwed it up to much I decided to uninstall and try again.

As the documentation on the XAMPP website doesn't say how to uninstall I just deleted the directory and went to reinstall with the command now i get endless errors when it tries to extract with 

tar xvfz xampp-linux-1.6.7.tar.gz -C /opt

All essentially reading No such file or directory. How do i reinstall XAMPP and get the files into the htdocs folder and working.

Please help I've got to demo a website tomorrow and I'm done for other wise i need this server working and I'm out of time.

Cheers SPR

---

### Post by drubin on 2008-09-17
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

try this method. (I prefer it to the xampp approche)

---

### Post by sands on 2008-09-17
Why XAMPP? I installed apache php and mysql from the repo..

Webroot will be located in /var/www

---

### Post by mrsteveman1 on 2008-09-17
I agree with the others, just install apache, php and mysql from the repo, its easier and it should work perfectly.

---


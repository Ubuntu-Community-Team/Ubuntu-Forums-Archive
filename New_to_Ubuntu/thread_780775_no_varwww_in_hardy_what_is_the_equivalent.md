---
title: "no var/www in hardy what is the equivalent"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by coolbeans on 2008-05-03
I am at a lost :confused: of where to put my webpages so I can view them on my localhost.  On Feisty I placed it in var/www.  Could someone provide some insight?

Thanks

Never mind i found out how but I can not delete this post

---

### Post by mrzaius on 2008-05-03
In case anyone else was wondering, it is still in /var/www

That said, here's how you check:
~$ grep DocumentRoot /etc/apache2/sites-available/*

	DocumentRoot /var/www/

That returns the DocumentRoot/local webroot of all available sites, using the standard Debian-style apache2 configuration.

---

### Post by Joeb454 on 2008-05-03
> **coolbeans said:**
> Never mind i found out how but I can not delete this post

Care to share how you solved the problem? :)

---

### Post by master5o1 on 2008-05-03
Just a basic question:

Do you *even* have Apache intalled?

Edit: Didn't notice it was solved XD

---


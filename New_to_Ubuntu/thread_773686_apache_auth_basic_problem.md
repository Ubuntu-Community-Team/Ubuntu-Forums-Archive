---
title: "apache auth_basic problem"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Bonta on 2008-04-29
I have ubuntu 8.04. Ive installed apache. I have a basic homepage, and another directory i want to protect with a password. I have a .htaccess file in there that I know used to work with a 3 year old version of fedora, but when I web to the directory it goes straight in without asking for a password.

What is the /etc/apache2/apache2.conf option to enable .htaccess checking?

---

### Post by spiderbatdad on 2008-04-29
I believe you want auth_basic in the sites-available/your_site file, as an option, under the appropriate Directory.

---

### Post by Bonta on 2008-04-29
! Thanks for that. Works now. apache's config file system is more complicated. :popcorn:

---

### Post by spiderbatdad on 2008-04-29
most stuff happens in sites-available and httpd.conf. I don't think you'll need to bother with apache2.conf for anything...

---


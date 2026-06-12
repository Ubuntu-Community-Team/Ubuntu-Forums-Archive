---
title: "XAMPP+Ubuntu &amp; Virtual Host"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by php-zbatev on 2008-06-14
I have just installed XAMPP and I wanted to implement Virtual Hosting in it, unfortunately for me, i had followed several ways already and nothing did work: this is how the essentials are setup:
[B]
my /etc/hosts has:[/B]
   127.0.0.1 myvirtualhost localhost

**my /extra/httpd-vhost.conf has:**
   NameVirtualHost *:80

   <VirtualHost *:80>
     ServerName myvirtualhost
     DocumentRoot /htdocs/myvirtualhostdocroot/
   </VirtualHost>

**what happens is that everytime i put this:**
   [http://myvirtualhost](http://myvirtualhost)
**the browser redirects me to:**
   [http://myvirtualhost/xampp](http://myvirtualhost/xampp)

**which i think is normal because of the index.html in /htdocs which has this line:**
   <meta http-equiv="refresh" content="0;url=/xampp/">

my question is am I doing the right thing? what should really be done... i really did tried different approaches already but here I am still struggling. Hope someone could help out.

---


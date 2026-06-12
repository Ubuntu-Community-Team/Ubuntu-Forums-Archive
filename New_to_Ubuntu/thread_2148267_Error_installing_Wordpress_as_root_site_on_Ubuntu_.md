---
title: "Error installing Wordpress as root site on Ubuntu Server 13.04"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by jrohde on 2013-05-24
Hi

I have installed Wordpress using this guide: [https://help.ubuntu.com/13.04/serverguide/wordpress.html](https://help.ubuntu.com/13.04/serverguide/wordpress.html). 

I want Wordpress to be available in the root, so I changed the two lines:

```
Alias /blog /usr/share/wordpress
Alias /blog/wp-content /var/lib/wordpress/wp-content
```

in this file: /etc/apache2/sites-available/wordpress 

to:

```
Alias / /usr/share/wordpress
Alias /wp-content /var/lib/wordpress/wp-content
```

but that wasn't enough, because I get no response from the URL http://<server>/wp-admin/install.php. 

What am I doing wrong?

Thanks
Jakob

---

### Post by lethall1 on 2013-05-24
```
sudo service apache2 restart
``` doesnt helps?

---

### Post by jrohde on 2013-05-24
Hi lethal1

No, that doesn't help, but I get this error message:

** [warn] The Alias directive in /etc/apache2/sites-enabled/wordpress at line 2 will probably never match because it overlaps an earlier Alias.**

Line 2 is this one: "Alias /wp-content /var/lib/wordpress/wp-content".

What does that mean?

/Jakob

---


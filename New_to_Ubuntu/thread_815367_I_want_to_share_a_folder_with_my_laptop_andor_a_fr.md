---
title: "I want to share a folder with my laptop and/or a friend via the internet"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by marmaladejackson on 2008-06-01
Hi all,

I want to share/make available a folder so I or a friend could access it remotely.  I just networked all the computers in my home and it was a breeze.  Is there an easy way to do this?  If so could somebody pint me in the right direction?

Thanks much!

---

### Post by steveneddy on 2008-06-01
The easy way would be to use Remote Desktop.

---

### Post by Prospero2006 on 2008-06-01
```
 
sudo apt-get install apache2

```

Then create a folder in /var/www
Create a .htaccess file that specifies a username and password.

(This will allow your friend to read, but not write.)

You could install proftpd.
You could create a user account for your friend and try something
like sshfs.

Just a few suggestions.

---


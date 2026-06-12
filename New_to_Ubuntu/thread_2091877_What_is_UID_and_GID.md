---
title: "What is UID and GID ?"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by honey_bee on 2012-12-06
hi,
       Can some one guide me that what is  UID,GID . When a user is created in ubuntu what is the default UID ? Normally UID 0 (Zero) is for the root user or the administrator. what about the user ID from rang 1 to 499 and from 500 to 1000 (If i am correct.)

Any site which can explain the ID values structure ?

thanks
honey

---

### Post by steeldriver on 2012-12-06
Maybe this section from the Debian Policy Manual?

[http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.2](http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.2)

Also, Ubuntu by default uses User Private Groups so you might want to do some reading about those

---

### Post by SeijiSensei on 2012-12-06
Ubuntu, as a Debian derivative, starts numbering users at 1000.  You're probably used to RedHat-flavored distros, where users begin at 500.  Since I use Ubuntu on the desktop and CentOS on my servers, I've had to copy over the user entries from my desktop's /etc/passwd to the server's /etc/passwd so I have the same permissions both places.  Usually that means using chown to renumber the home directories on the server as well.  However most user management tools like useradd will just give a new user the UID immediately following the last one in the file.  So even on the CentOS machine, if I add a new user, that person will be assigned a number in the 1000+ range.

---


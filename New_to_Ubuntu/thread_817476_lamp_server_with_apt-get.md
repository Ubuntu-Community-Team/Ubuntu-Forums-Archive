---
title: "lamp server with apt-get"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-06-03
Does anyone know how to get a lamp server going using apt-get (so no XAMPP).  I have XAMPP going right now but I'd rather have PHP and Apache installed from apt-get so they can be updated with the rest of my system.  Does anyone know all of the different things I'd need to apt-get in order to get lamppp going? (apache, mysql, php, perl,proftpd)?

---

### Post by cpetercarter on 2008-06-03
Have a look at this - [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by newbuntuxx on 2008-06-03
open terminal and type:


```
sudo tasksel install lamp-server
```

follow instructions. Make sure you enter a password for your mysql root user, and make sure you remember that password.

---


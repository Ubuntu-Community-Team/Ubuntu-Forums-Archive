---
title: "Forbidden Access"
date: 2008-03-05
forum: Programming Talk
---

### Post by mmarif4u on 2008-03-05
I changed the root directory from xampp directory to media/disk/www.
When now i try to access the pages.it redirect me to the forbidden page:
> 
Forbidden
You don't have permission to access /dbkl_bm on this server.

Everything is working fine.Dont know how to solve it.
Any help will be appreciated.

---

### Post by mssever on 2008-03-05
You didn't provide very much info, so I'm having to guess here.

First, why use XAMPP under Linux? Using the real deal is much better, and it's easier to install than XAMPP. XAMPP is great for Windows. Either install the packages you need ```
sudo aptitude install apache2 php5 mysql-server php5-mysql
``` or use tasksel for an even easier experience: ```
sudo tasksel
```

As far as 403 Forbidden errors go, a common cause is incorrect permissions--on the file in question or its directory (or parent directories).

---

### Post by mmarif4u on 2008-03-05
thanks alot for ur tips.
i got it working by ur method.
Easy and fast.

---


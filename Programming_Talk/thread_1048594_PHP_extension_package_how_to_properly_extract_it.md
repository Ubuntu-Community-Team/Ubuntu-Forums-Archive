---
title: "PHP extension package: how to properly extract it?"
date: 2009-01-23
forum: Programming Talk
---

### Post by zpzpzp on 2009-01-23
I have downloaded this package:
[http://pear.php.net/package/DBA_Relational/download/](http://pear.php.net/package/DBA_Relational/download/)

However when I extracted the package using WinRAR, I see only one file that has no extension name. Should I see some .php files instead?

I think I am doing something wrong here. I would appreciate any advise.

Thanks a lot.

Paul

---

### Post by Reiger on 2009-01-23
If it is a PECL extension you use PECL

And you don't download the package manually, you simply type:
```
pecl install <package_name>
```

If it is a PEAR package you use PEAR

Likewise, you don't download stuff manually:
```
pear install <package_name>
```

---

### Post by Tibuda on 2009-01-23
Better use sudo when installing these commands Reiger told you.

---

### Post by zpzpzp on 2009-02-17
Thank you Reiger and Danielrmt.

I am using windows machine and I get this following error:

> C:\xampp\php>pecl install Zip
No releases available for package "pecl.php.net/Zip"
Cannot initialize 'channel://pecl.php.net/Zip', invalid or missing package file
Package "channel://pecl.php.net/Zip" is not valid
install failed

Does anyone know why?

Thanks in advance!

---


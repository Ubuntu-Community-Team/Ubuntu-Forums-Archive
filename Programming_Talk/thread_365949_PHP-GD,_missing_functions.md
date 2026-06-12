---
title: "PHP-GD, missing functions?"
date: 2007-02-20
forum: Programming Talk
---

### Post by colinrotherham on 2007-02-20
Using the PHP reference for imageconvolution:
[http://uk2.php.net/imageconvolution](http://uk2.php.net/imageconvolution)

The function imageconvolution is supposed to be included from php 5.1 and up, i've got the latest php and php-gd package using apt-get which phpinfo() reports as 5.1.6 using gd version 2.0 or higher.

I get the error 'Call to undefined function imageconvolution()' but when I use my paid web-hosting (same version of php, but gd 2.0.28 compatible) it works fine.

Any idea why it's not working for me? Is there a version of php/php-gd I can download where it will?

Thanks

---

### Post by Randomskk on 2007-02-20
Ubuntu doesn't compile PHP's GD for security reasons. It instead uses generic GD. Therefore, a lot of PHP GD functions are not available.
There are somewhat valid security reasons at play here, but to get it working yourself you'll need to compile your own PHP, and enable GD on it.

---

### Post by colinrotherham on 2007-02-20
Ahh now that explains it, thanks

---

### Post by Mgccl on 2007-03-01
[http://mgccl.com/2007/03/02/simple-replication-of-imageconvolution-function](http://mgccl.com/2007/03/02/simple-replication-of-imageconvolution-function)

that site have a PHP replication of the imageconvolution function, but it's 50 times slower than the Bundled GD version

---

### Post by charbelbg on 2010-03-02
Hi Guys, any idea on how to recomple PHP on ubuntu, I added the GD libs to PHP but as you said above many functions are not working.....
How can I recomplie PHP?

---

### Post by CyberJack on 2010-03-02
Here is how you can compile php on ubuntu with gd support:
[http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu](http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu)

---

### Post by charbelbg on 2010-03-02
thanks for your reply, but I still have one question?? am I going to loose anyting? files, settings, virtual hosts?
and what are the chances that the ubuntu will be down as a web server because we cant afford that for the time being?

---

### Post by CyberJack on 2010-03-02
As far a I know you won't loose anything when you recompile php.
Recompiling will just generate some deb files which you have to install manually.

If you only need the GD functionality you just have to install the php-gd deb file.
That will only overwrite the currently installed php-gd library.

Afterward you should reload the webserver (for example apache) so the new gd library is used.

---


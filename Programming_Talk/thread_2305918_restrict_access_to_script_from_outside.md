---
title: "restrict access to script from outside"
date: 2015-12-10
forum: Programming Talk
---

### Post by udragu on 2015-12-10
Hello All!

There is a problem: I need to restrict access to PHP-5 script  from outside.
The main goal is to achieve that  only scripts on the same  virtual host can pass  POST query to this first script.

$_SERVER['REMOTE_ADDR']=='127.0.0.1' I guess that is not solution. I think that curl can avoid it.

Environment: 
Apache Version Apache/2.2.22
php 5.6.3
system: ubuntu server 14.04 64bit

Thnx!

---

### Post by SeijiSensei on 2015-12-10
One solution is to put the script in a separate subdirectory and use the [Require]("http://httpd.apache.org/docs/2.4/howto/access.html") directive in Apache:
```

<VirtualHost *:80>
[stuff]
Alias /secretscripts /var/www/scripts
<Directory "/var/www/scripts">
     Require 127.0.0.1
</Directory>
[stuff]
</VirtualHost>

```

Now only the local machine can issue a request to [http://localhost/secretscripts/myscript.php](http://localhost/secretscripts/myscript.php).

---

### Post by udragu on 2015-12-11
Thanks!
I understand, that's working!

---


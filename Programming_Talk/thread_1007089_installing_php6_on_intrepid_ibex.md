---
title: "installing php6 on intrepid ibex"
date: 2008-12-10
forum: Programming Talk
---

### Post by adaykin on 2008-12-10
Hello, I'm new to ubuntu, and I'm having problems installing php6. When I run the sudo make install for php, I get an error message saying:

```

Installing PHP SAPI module:       apache2handler
/usr/share/apache2/build/instdso.sh SH_LIBTOOL='/usr/share/apr-1.0/build/libtool' libphp6.la /usr/lib/apache2/modules
/usr/share/apr-1.0/build/libtool --mode=install cp libphp6.la /usr/lib/apache2/modules/
cp .libs/libphp6.so /usr/lib/apache2/modules/libphp6.so
cp .libs/libphp6.lai /usr/lib/apache2/modules/libphp6.la
libtool: install: warning: remember to run `libtool --finish /home/adaykin/php_source/php6.0-200812100530/libs'
chmod 644 /usr/lib/apache2/modules/libphp6.so
apxs:Error: Activation failed for custom /etc/apache2/httpd.conf file..
apxs:Error: At least one `LoadModule' directive already has to exist..
make: *** [install-sapi] Error 1


```

I tried putting on dummy module in my httpd.conf file, and then restarted apache, but I still got the error.

---


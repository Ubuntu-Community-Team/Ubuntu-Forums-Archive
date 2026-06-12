---
title: "Failure recompiling PHP from source - no libphp5.so!"
date: 2006-09-27
forum: Programming Talk
---

### Post by Saeven on 2006-09-27
Hi everyone.

As a previous Slackware user, I'm no newbie to Linux - Ubuntu is a nice system, but it definitely is being a ](*,) where custom compilation is concerned.  I need to have a 'buildable' PHP source tree, and this is usually a no brainer.  Unfortunately on Ubuntu, it's apparently real PITA.

I have used synaptic to install apache-mpm-prefork and the dev headers (this is after the problem occurred when installing Apache 1.3.37 from source as well) thinking I might get a successful build.

PHP compilation goes well, no problems at all.  When I get to make install however, here's what happens:

> 
Installing PHP SAPI module:       apache2handler
/usr/share/apache2/build/instdso.sh SH_LIBTOOL='/usr/bin/libtool' libphp5.la /usr/lib/apache2/modules
/usr/bin/libtool --mode=install cp libphp5.la /usr/lib/apache2/modules/
cp .libs/libphp5.lai /usr/lib/apache2/modules/libphp5.la
cp .libs/libphp5.a /usr/lib/apache2/modules/libphp5.a
chmod 644 /usr/lib/apache2/modules/libphp5.a
ranlib /usr/lib/apache2/modules/libphp5.a
libtool: install: warning: remember to run `libtool --finish /devel/php-5.1.6/libs'
Warning!  dlname not found in /usr/lib/apache2/modules/libphp5.la.
Assuming installing a .so rather than a libtool archive.
chmod 644 /usr/lib/apache2/modules/libphp5.so
chmod: cannot access `/usr/lib/apache2/modules/libphp5.so': No such file or directory
apxs:Error: Command failed with rc=65536
.
make: *** [install-sapi] Error 1


The whole 'make' process runs through without a peep.  A+  Why this catastrophe?  How can it be fixed?

Ubuntu expertise most appreciated!  Gurus out of the woodwork be summoned!

Thanks.
Alex
Why is it giving this error?

---


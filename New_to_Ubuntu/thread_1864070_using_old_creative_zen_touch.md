---
title: "using old creative zen touch"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by seanpmccclellan on 2011-10-18
Hey,

I'm trying to put music on a zen creative touch and i am running ubuntu 11.04. 

I'm having trouble installing libnjb. I downloaded the .tar.gz and unpacked it. I've gone into the directory and run

./configure

and then

make

These seem to go fine.

When i i run

make install

It tells me:

Making install in src
make[1]: Entering directory `/home/sean/libnjb-2.2.7/src'
make[2]: Entering directory `/home/sean/libnjb-2.2.7/src'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libnjb.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libnjb.so.5.1.1 /usr/local/lib/libnjb.so.5.1.1
/usr/bin/install: cannot create regular file `/usr/local/lib/libnjb.so.5.1.1': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/sean/libnjb-2.2.7/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/sean/libnjb-2.2.7/src'
make: *** [install-recursive] Error 1

What should I do?

---


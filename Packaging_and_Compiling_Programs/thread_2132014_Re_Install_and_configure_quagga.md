---
title: "Re: Install and configure quagga"
date: 2013-04-03
forum: Packaging and Compiling Programs
---

### Post by shahnejat on 2013-04-03
Hi guys,
I'm trying to compile(necessary to compile from scratch) quagga-0.98.5 but meanwhile encountering some problems. Anybody? Any solutions?

Thanks

gcc -DHAVE_CONFIG_H -DSYSCONFDIR=\"/usr/local/etc/\" -I. -I. -I.. -I.. -I.. -I../lib -Os -g -Wall -Wsign-compare -Wpointer-arith -Wbad-function-cast -Wwrite-strings -MT sockopt.lo -MD -MP -MF .deps/sockopt.Tpo -c sockopt.c  -fPIC -DPIC -o .libs/sockopt.o
sockopt.c: In function 'getsockopt_ipv6_ifindex':
sockopt.c:150:17: error: dereferencing pointer to incomplete type
sockopt.c:151:1: warning: control reaches end of non-void function [-Wreturn-type]
make[2]: *** [sockopt.lo] Error 1
make[2]: Leaving directory `/quagga-0.98.5/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/quagga-0.98.5'
make: *** [all] Error 2

---

### Post by oldos2er on 2013-04-03
Moved to Packaging & Compiling Programs.

---

### Post by schragge on 2013-04-03
Would recompiling a source deb from Ubuntu repository be an option? Or at least re-using its infrastructure?

---


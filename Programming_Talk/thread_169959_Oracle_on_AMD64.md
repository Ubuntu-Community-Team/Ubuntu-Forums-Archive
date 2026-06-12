---
title: "Oracle on AMD64"
date: 2006-05-03
forum: Programming Talk
---

### Post by remohammadi on 2006-05-03
I have a problem in installation. in Linking 'Oracle Database 10g 10.2.0.1.0' step.
The message is :

[SIZE="1"]Exception Name: MakefileException
Exception String: Error in invoking target 'install' of makefile '/share/app/oracle/product10_1/ctx/lib/ins_ctx.mk'. See '/share/app/oracle/oraInventory/logs/installActions2006-05-03_09-01-16PM.log' for details.[/SIZE]

tail of '/share/app/oracle/product10_1/install/make.log' :

[SIZE="1"]gcc **-m32** -o **ctxhx** -L/share/app/oracle/product10_1/ctx//lib32/ -L/share/app/oracle/product10_1/lib32/ -L/share/app/oracle/product10_1/lib32/stubs/  /share/app/oracle/product10_1/ctx/lib/ctxhx.o -L/share/app/oracle/product10_1/ctx/lib/ -ldl -lm -lctxhx -Wl,-rpath,/share/app/oracle/product10_1/ctx/lib -lsnls10 -lnls10  -lcore10 -lsnls10 -lnls10 -lcore10 -lsnls10 -lnls10 -lxml10 -lcore10 -lunls10 -lsnls10 -lnls10 -lcore10 -lnls10  `cat /share/app/oracle/product10_1/lib/sysliblist`[/SIZE]

/usr/bin/ld: skipping incompatible /lib/libpthread.so.0 when searching for /lib/libpthread.so.0
/usr/bin/ld: cannot find /lib/libpthread.so.0
collect2: ld returned 1 exit status
make: *** [ctxhx] Error 1

I'm using **AMD64**, so my /lib/libpthread.so.0 is 64 bit.
LD_LIBRARY_PATH=/usr/lib:/usr/lib32:/share/app/oracle/product/10.1.0.3/db_1/lib
and /etc/ld.so.conf contains /lib32

Can anybody help me, please?!! ](*,) :neutral:

---

### Post by xbalanque on 2006-06-28
Same problem here :( Did you find a way around it ? 

thx :)

---

### Post by remohammadi on 2006-06-28
I switched to Fedora 5 :-\" 
There was some other problems but I found howto for that.

---


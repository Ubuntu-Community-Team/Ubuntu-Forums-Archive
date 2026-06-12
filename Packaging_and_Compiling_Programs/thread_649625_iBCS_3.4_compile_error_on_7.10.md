---
title: "iBCS 3.4 compile error on 7.10"
date: 2007-12-25
forum: Packaging and Compiling Programs
---

### Post by dimitar_ on 2007-12-25
Hi all,

I am having problems while trying to compile iBSC 3.4.I need this tool to enable SCO Unix compatibility that runs an old Acu Cobol application.
Maybe someone has another idea how to run this acu cobol app on linux ???
 Here is the error on compiling;

make -C /lib/modules/2.6.22-14-generic/build M=/home/smokie/Desktop/ibcs-3_4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/smokie/Desktop/ibcs-3_4/svr4/socksys.o
In file included from /home/smokie/Desktop/ibcs-3_4/svr4/socksys.c:51:
/home/smokie/Desktop/ibcs-3_4/svr4/../include/util/revalidate.h: In function ‘do_revalidate’:
/home/smokie/Desktop/ibcs-3_4/svr4/../include/util/revalidate.h:32: warning: passing argument 2 of ‘notify_change’ from incompatible pointer type
/home/smokie/Desktop/ibcs-3_4/svr4/../include/util/revalidate.h:32: error: too few arguments to function ‘notify_change’
make[3]: *** [/home/smokie/Desktop/ibcs-3_4/svr4/socksys.o] Error 1
make[2]: *** [/home/smokie/Desktop/ibcs-3_4/svr4] Error 2
make[1]: *** [_module_/home/smokie/Desktop/ibcs-3_4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2


Thanks,

---


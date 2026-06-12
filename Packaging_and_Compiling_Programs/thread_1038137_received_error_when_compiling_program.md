---
title: "received error when compiling program"
date: 2009-01-12
forum: Packaging and Compiling Programs
---

### Post by newbux on 2009-01-12
hello i was doing a tutorial at [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472) and i think i did everything correctly and i compiled this application snort and received a error message i am at a loss of what to do now can you help out some of it compiled but thier was this error at the end

terminal code in tutorial:

cd /usr/src/snort-2.8.3
./configure -enable-dynamicplugin --with-mysql
make
make install

error:

In function ‘open’,
inlined from ‘server_stats_save’ at server_stats.c:349:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[4]: *** [server_stats.o] Error 1
make[4]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors/flow/portscan'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors/flow'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/snort-2.8.3.1/src'
make: *** [install-recursive] Error 1

thanks

---


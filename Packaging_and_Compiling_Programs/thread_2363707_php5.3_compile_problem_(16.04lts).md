---
title: "php5.3 compile problem (16.04lts)"
date: 2017-06-13
forum: Packaging and Compiling Programs
---

### Post by tmg2 on 2017-06-13
Hello 


I am using Ubuntu 16.04. I need to compile php5.3. It's necessary for a job. 
However, I am getting mistakes like the following when I compile. 


Can you help me with this?


Errors:
/usr/bin/ld: warning: libkrb5.so.26, needed by //usr/lib/x86_64-linux-gnu/libgssapi.so.3, may conflict with libkrb5.so.3
ext/mysqli/mysqli.o: In function `php_local_infile_read':
/home/gokan/php-5.3.27/ext/mysqli/mysqli.c:1419: undefined reference to `client_errors'
ext/mysqli/mysqli.o: In function `memcpy':
/usr/include/x86_64-linux-gnu/bits/string3.h:53: undefined reference to `client_errors'
/usr/include/x86_64-linux-gnu/bits/string3.h:53: undefined reference to `client_errors'
/usr/include/x86_64-linux-gnu/bits/string3.h:53: undefined reference to `client_errors'
ext/mysqli/mysqli.o: In function `php_local_infile_init':
/home/gokan/php-5.3.27/ext/mysqli/mysqli.c:1372: undefined reference to `client_errors'
ext/mysqli/mysqli.o:/home/gokan/php-5.3.27/ext/mysqli/mysqli.c:1495: more undefined references to `client_errors' follow
collect2: error: ld returned 1 exit status
Makefile:275: recipe for target 'sapi/fpm/php-fpm' failed
make: *** [sapi/fpm/php-fpm] Error 1

---


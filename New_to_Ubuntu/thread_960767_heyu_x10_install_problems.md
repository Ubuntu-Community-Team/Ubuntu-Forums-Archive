---
title: "heyu x10 install problems"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by xsilvergs on 2008-10-27
Hi
I've managed to install heyu which is an x10 home automation controller on to my old laptop which runs Ubuntulite without difficulty but when I try to install onto Intrepid I get errors.

If it installs on one machine is it a permissions problem and how do I overcome it?

Thank you

Tony

Here is a copy from Terminal:

tony@BlackUbuntu:~/heyu-2.3.2$ ./Configure

This script will create a Makefile based by default on
the output of uname(1), or otherwise on the system type
parameter you enter.
 
The Makefile has been created for linux.

Note: If you are upgrading from an earlier version,
run 'heyu stop' before proceeding further.

** Now run 'make' as a normal user **

tony@BlackUbuntu:~/heyu-2.3.2$ make
gcc -g -O -DSYSV -DPOSIX -DHAS_ITIMER -DLINUX -DHASSELECT -DHASTZ -DHASCM17A -DHASEXT0 -DHASRFXS -DHASRFXM -DHASDMX -DHASORE -Wall   -c -o date.o date.c
gcc -g -O -DSYSV -DPOSIX -DHAS_ITIMER -DLINUX -DHASSELECT -DHASTZ -DHASCM17A -DHASEXT0 -DHASRFXS -DHASRFXM -DHASDMX -DHASORE -Wall   -c -o erase.o erase.c
gcc -g -O -DSYSV -DPOSIX -DHAS_ITIMER -DLINUX -DHASSELECT -DHASTZ -DHASCM17A -DHASEXT0 -DHASRFXS -DHASRFXM -DHASDMX -DHASORE -Wall   -c -o info.o info.c
gcc -g -O -DSYSV -DPOSIX -DHAS_ITIMER -DLINUX -DHASSELECT -DHASTZ -DHASCM17A -DHASEXT0 -DHASRFXS -DHASRFXM -DHASDMX -DHASORE -Wall   -c -o message.o message.c
gcc -g -O -DSYSV -DPOSIX -DHAS_ITIMER -DLINUX -DHASSELECT -DHASTZ -DHASCM17A -DHASEXT0 -DHASRFXS -DHASRFXM -DHASDMX -DHASORE -Wall   -c -o relay.o relay.c
relay.c: In function ‘start_relay’:
relay.c:240: warning: format not a string literal and no format arguments
relay.c:301: warning: ignoring return value of ‘ftruncate’, declared with attribute warn_unused_result
relay.c:354: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
relay.c:364: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
relay.c:369: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
relay.c:387: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
relay.c:415: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
relay.c:426: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
relay.c:433: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc -g -O -DSYSV -DPOSIX -DHAS_ITIMER -DLINUX -DHASSELECT -DHASTZ -DHASCM17A -DHASEXT0 -DHASRFXS -DHASRFXM -DHASDMX -DHASORE -Wall   -c -o monitor.o monitor.c
In file included from /usr/include/fcntl.h:217,
                 from monitor.c:86:
/usr/include/bits/fcntl2.h: In function ‘c_monitor’:
/usr/include/bits/fcntl2.h:43: error: nested function ‘open’ declared ‘extern’
/usr/include/bits/fcntl2.h:42: error: static declaration of ‘open’ follows non-static declaration
/usr/include/fcntl.h:85: error: previous declaration of ‘open’ was here
make: *** [monitor.o] Error 1
tony@BlackUbuntu:~/heyu-2.3.2$

---

### Post by xsilvergs on 2008-10-31
All sorted.

Charles Sullivan who wrote Heyu has updated his code to work with Intrepid.

---

### Post by wa0tko on 2008-11-01
Version 2.3.2 still gives the same fcntl.h error on 8.10 Intrepid.

---

### Post by StreetsBolted on 2010-08-14
I installed heyu 2.9.0 on Ubuntu 9.04 by running make install then apt-get install build-essential.  It looks like it installed, no errors.  There's no menu items though so how do I run it?  Have I completed the install?

---


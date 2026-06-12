---
title: "problem with make"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by dezeGno on 2008-05-29
Hi there, I got a problem with the make command, I get this error every time I try to use it.
vilhjalmur@vilhjalmur-desktop:~/psybnc$ make menuconfig
Initializing Menu-Configuration
[*] Running Conversion Tool for older psyBNC Data.
Using existent configuration File.
[*] Running Autoconfig.
System: Linux
Socket Libs: Internal.
Environment: Internal.
Time-Headers: in time.h and sys/time.h
Byte order: Big Endian.
IPv6-Support: Yes.
async-DNS-Support: Yes.
SSL-Support: No openssl found. Get openssl at [www.openssl.org](www.openssl.org)
Creating Makefile
[*] Creating Menu, please wait.
This needs the ncurses library. If it is not available, menuconf wont work. If you are using curses, use make menuconfig-curses instead.
make: *** [menuconfig] Error 1
vilhjalmur@vilhjalmur-desktop:~/psybnc$ 

Any help?

---

### Post by finer recliner on 2008-05-29
this application uses a library that you do not have installed. this is called a dependency. You are missing ncurses in this case.

i believe the package you want is libncurses5.

install it using:
```
sudo apt-get install libncurses5
```

you may be missing more dependencies. check the application's main website for more info.

---


---
title: "/dbus-glib-0.71 installation"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by hawas on 2008-10-03
Hi all
I´ve been trying to install vlc media player on ubuntu. But is requires a few dependencies and one of them is something called dbusglib
I tried installing it from [https://launchpad.net/ubuntu/edgy/+source/dbus-glib/0.71-1](https://launchpad.net/ubuntu/edgy/+source/dbus-glib/0.71-1) (that tar.gz file).
However, the installation doesnt complete. After configuring the files, when I try to give the make command, this is the error message that I get. S.O.S someone...please 


hawas@ubuntu:~/Desktop/dbus-glib-0.71$ sudo make
make  all-recursive
make[1]: Entering directory `/home/hawas/Desktop/dbus-glib-0.71'
Making all in dbus
make[2]: Entering directory `/home/hawas/Desktop/dbus-glib-0.71/dbus'
make  all-recursive
make[3]: Entering directory `/home/hawas/Desktop/dbus-glib-0.71/dbus'
Making all in .
make[4]: Entering directory `/home/hawas/Desktop/dbus-glib-0.71/dbus'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I..  -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -DDBUS_COMPILATION=1 -DDBUS_LOCALEDIR=\"/usr/local/share/locale\"   -DDBUS_API_SUBJECT_TO_CHANGE=1   -g -O2 -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wfloat-equal -Wsign-compare -MT dbus-glib.lo -MD -MP -MF ".deps/dbus-glib.Tpo" -c -o dbus-glib.lo dbus-glib.c; \
        then mv -f ".deps/dbus-glib.Tpo" ".deps/dbus-glib.Plo"; else rm -f ".deps/dbus-glib.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DDBUS_COMPILATION=1 -DDBUS_LOCALEDIR=\"/usr/local/share/locale\" -DDBUS_API_SUBJECT_TO_CHANGE=1 -g -O2 -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wfloat-equal -Wsign-compare -MT dbus-glib.lo -MD -MP -MF .deps/dbus-glib.Tpo -c dbus-glib.c  -fPIC -DPIC -o .libs/dbus-glib.o
In file included from dbus-glib.c:25:
dbus-glib.h:28:30: error: dbus/dbus-shared.h: No such file or directory
In file included from dbus-glib.c:25:
dbus-glib.h:74: error: expected ')' before 'type'
In file included from dbus-glib.c:26:
dbus-glib-lowlevel.h:28:23: error: dbus/dbus.h: No such file or directory
In file included from dbus-glib.c:26:
dbus-glib-lowlevel.h:33: error: expected declaration specifiers or '...' before 'DBusError'
dbus-glib-lowlevel.h:42: error: expected ')' before '*' token
dbus-glib-lowlevel.h:44: error: expected ')' before '*' token
dbus-glib-lowlevel.h:48: error: expected declaration specifiers or '...' before 'DBusMessage'
dbus-glib-lowlevel.h:49: error: expected declaration specifiers or '...' before 'dbus_uint32_t'
dbus-glib-lowlevel.h:51: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
dbus-glib-lowlevel.h:52: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
dbus-glib-lowlevel.h:62: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
dbus-glib-lowlevel.h:65: error: expected declaration specifiers or '...' before 'DBusMessage'
In file included from dbus-glib.c:29:
dbus-gobject.h:27:33: error: dbus/dbus-signature.h: No such file or directory
dbus-glib.c: In function 'dbus_g_connection_flush':
dbus-glib.c:49: warning: implicit declaration of function 'dbus_connection_flush'
dbus-glib.c:49: warning: nested extern declaration of 'dbus_connection_flush'
dbus-glib.c:49: error: 'DBusConnection' undeclared (first use in this function)
dbus-glib.c:49: error: (Each undeclared identifier is reported only once
dbus-glib.c:49: error: for each function it appears in.)
dbus-glib.c:49: error: expected expression before ')' token
dbus-glib.c: In function 'dbus_g_connection_ref':
dbus-glib.c:61: error: 'DBusConnection' undeclared (first use in this function)
dbus-glib.c:61: error: 'c' undeclared (first use in this function)
dbus-glib.c:63: error: expected expression before ')' token
dbus-glib.c:64: warning: implicit declaration of function 'dbus_connection_ref'
dbus-glib.c:64: warning: nested extern declaration of 'dbus_connection_ref'
dbus-glib.c: In function 'dbus_g_connection_unref':
dbus-glib.c:77: error: 'DBusConnection' undeclared (first use in this function)
dbus-glib.c:77: error: 'c' undeclared (first use in this function)
dbus-glib.c:79: error: expected expression before ')' token
dbus-glib.c:80: warning: implicit declaration of function 'dbus_connection_unref'
dbus-glib.c:80: warning: nested extern declaration of 'dbus_connection_unref'
dbus-glib.c: In function 'dbus_g_message_ref':
dbus-glib.c:93: error: 'DBusMessage' undeclared (first use in this function)
dbus-glib.c:93: error: 'c' undeclared (first use in this function)
dbus-glib.c:95: error: expected expression before ')' token
dbus-glib.c:96: warning: implicit declaration of function 'dbus_message_ref'
dbus-glib.c:96: warning: nested extern declaration of 'dbus_message_ref'
dbus-glib.c: In function 'dbus_g_message_unref':
dbus-glib.c:108: error: 'DBusMessage' undeclared (first use in this function)
dbus-glib.c:108: error: 'c' undeclared (first use in this function)
dbus-glib.c:110: error: expected expression before ')' token
dbus-glib.c:111: warning: implicit declaration of function 'dbus_message_unref'
dbus-glib.c:111: warning: nested extern declaration of 'dbus_message_unref'
dbus-glib.c: In function 'dbus_connection_get_g_type':
dbus-glib.c:189: error: 'dbus_connection_ref' undeclared (first use in this function)
dbus-glib.c:190: error: 'dbus_connection_unref' undeclared (first use in this function)
dbus-glib.c: In function 'dbus_message_get_g_type':
dbus-glib.c:207: error: 'dbus_message_ref' undeclared (first use in this function)
dbus-glib.c:208: error: 'dbus_message_unref' undeclared (first use in this function)
dbus-glib.c: At top level:
dbus-glib.c:255: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
dbus-glib.c:267: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make[4]: *** [dbus-glib.lo] Error 1
make[4]: Leaving directory `/home/hawas/Desktop/dbus-glib-0.71/dbus'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/hawas/Desktop/dbus-glib-0.71/dbus'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/hawas/Desktop/dbus-glib-0.71/dbus'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hawas/Desktop/dbus-glib-0.71'
make: *** [all] Error 2
hawas@ubuntu:~/Desktop/dbus-glib-0.71$ 

P.S: I am a total newbie...

---

### Post by hawas on 2008-10-03
oh well..*sheepish look* think I´ve got the error..thanks anyways!


_____________________
To forgive is to suffer

---

### Post by acharyayogesh on 2008-10-15
Hi,
I am also facing the same problem...
can u tell me how to fix this problem...

Thanks.

---


---
title: "Compiling from Source -Make errors"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by venture on 2008-08-04
I have downloaded a program from sourceforge called namot. I have placed the extracted file in the /etc directory (/etc/namot-2.2.0-pre4)

In the console I change directories (cd /etc/namot2.2.0-pre4)
I configure the file (./configure)
I check through all of the code looking for any buried errors
There are none
Now I type make
There are several errors and make does not complete
Can anyone identify the source of the errors



[root@andLinux namot-2.2.0-pre4]# make
make  all-recursive
make[1]: Entering directory `/etc/namot-2.2.0-pre4'
Making all in src
make[2]: Entering directory `/etc/namot-2.2.0-pre4/src'
source='graphics.c' object='_pynamot_la-graphics.lo' libtool=yes \
        depfile='.deps/_pynamot_la-graphics.Plo' tmpdepfile='.deps/_pynamot_la-graphics.TPlo' \
        depmode=gcc3 /bin/sh ../depcomp \
        /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -DLIB_HOME="\"/usr/local/share/namot\"" -DHELP_FILE_DIR="\"/usr/local/share/namot\"" -I/usr/include/python2.5 -I/usr/lib/python2.5/config -g -O2 -c -o _pynamot_la-graphics.lo `test -f 'graphics.c' || echo './'`graphics.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLIB_HOME=\"/usr/local/share/namot\" -DHELP_FILE_DIR=\"/usr/local/share/namot\" -I/usr/include/python2.5 -I/usr/lib/python2.5/config -g -O2 -c graphics.c -MT _pynamot_la-graphics.lo -MD -MP -MF .deps/_pynamot_la-graphics.TPlo  -fPIC -DPIC -o _pynamot_la-graphics.lo
In file included from /usr/include/zlib.h:34,
                 from /usr/include/png.h:383,
                 from graphics.c:35:
/usr/include/zconf.h:328: error: duplicate 'unsigned'
/usr/include/zconf.h:328: error: two or more data types in declaration specifiers
make[2]: *** [_pynamot_la-graphics.lo] Error 1
make[2]: Leaving directory `/etc/namot-2.2.0-pre4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/etc/namot-2.2.0-pre4'
make: *** [all] Error 2
[root@andLinux namot-2.2.0-pre4]#

---

### Post by Bachstelze on 2008-08-04
This looks very much like a bug in the software. Try another version.

But why on earth did you put the source in /etc ? It certainly does not belong there. Remove that directory, and keep the source in your home.

---

### Post by ibuclaw on 2008-08-04
You should never compile anything as root.

Download the tarball into your ~/src folder or ~/Desktop, extract, configure and make without the use of sudo.

If it builds successfully, **then** you may use "sudo make install"

Regards
Iain

---


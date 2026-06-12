---
title: "WHY? -- /usr/bi/ld: cannot find -lpython3.2"
date: 2011-03-07
forum: Packaging and Compiling Programs
---

### Post by myles2007 on 2011-03-07
For the last couple of days I have been trying to install mod_wsgi3.3 and Python3.2 on my Ubuntu box without success.

Installing mod_wsgi3.2 through apt-get works just fine, but I want to use mod_wsgi3.3 and Python 3.2.

I installed Python3.2 from source using './configure --enable-shared --prefix=/usr/' and all appears to be well with that installation (i.e., it works if I run python3 or python3.2 from the command line). My issue is with mod_wsgi3.3.

After running './configure --with-python=/usr/bin/python3', I get the following output from make:

```
/usr/bin/apxs2 -c -I/usr/include/python3.2m -DNDEBUG   mod_wsgi.c -L/usr/lib -L/usr/lib/python3.2/config  -lpython3.2 -lpthread -ldl  -lutil -lm
/usr/share/apr-1.0/build/libtool --silent --mode=compile --tag=disable-static i686-linux-gnu-gcc -prefer-pic -DLINUX=2 -D_FORTIFY_SOURCE=2 -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -D_REENTRANT -I/usr/include/apr-1.0 -I/usr/include/openssl -I/usr/include/xmltok -pthread     -I/usr/include/apache2  -I/usr/include/apr-1.0   -I/usr/include/apr-1.0  -I/usr/include/python3.2m -DNDEBUG  -c -o mod_wsgi.lo mod_wsgi.c && touch mod_wsgi.slo
In file included from /usr/include/python3.2m/Python.h:8,
                 from mod_wsgi.c:135:
/usr/include/python3.2m/pyconfig.h:1170: warning: "_POSIX_C_SOURCE" redefined
/usr/include/features.h:162: note: this is the location of the previous definition
/usr/include/python3.2m/pyconfig.h:1192: warning: "_XOPEN_SOURCE" redefined
/usr/include/features.h:164: note: this is the location of the previous definition
mod_wsgi.c: In function ‘Adapter_environ’:
mod_wsgi.c:3601: warning: assignment makes pointer from integer without a cast
mod_wsgi.c: In function ‘Dispatch_environ’:
mod_wsgi.c:8372: warning: assignment makes pointer from integer without a cast
mod_wsgi.c: In function ‘Auth_environ’:
mod_wsgi.c:13375: warning: assignment makes pointer from integer without a cast
/usr/share/apr-1.0/build/libtool --silent --mode=link --tag=disable-static i686-linux-gnu-gcc -o mod_wsgi.la  -rpath /usr/lib/apache2/modules -module -avoid-version    mod_wsgi.lo -L/usr/lib -L/usr/lib/python3.2/config -lpython3.2 -lpthread -ldl -lutil -lm
/usr/bin/ld: cannot find -lpython3.2
collect2: ld returned 1 exit status
apxs:Error: Command failed with rc=65536
```

I've searched quite a bit for a solution to this problem with no success. Does anyone have a solution for me?  When answering, please keep in mind that I'm fairly new to all of this and may not fairly basic instruction on some things.

Thanks in advance!!

---

### Post by MadCow108 on 2011-03-08
where is your libpython3.2 located?
it is searching in /usr/lib/python3.2/config

---

### Post by mbouza on 2011-03-16
I'am trying to compile mod_wsgi 3.3 with python 3.2 and am getting the same error:
```

/usr/bin/apxs2 -c -I/usr/local/include/python3.2m -DNDEBUG   mod_wsgi.c -L/usr/local/lib -L/usr/local/lib/python3.2/config  -lpython3.2 -lpthread -ldl  -lutil -lm
/usr/share/apr-1.0/build/libtool --silent --mode=compile --tag=disable-static i486-linux-gnu-gcc -prefer-pic -DLINUX=2 -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -D_REENTRANT -I/usr/include/apr-1.0 -I/usr/include/mysql -I/usr/include/openssl -I/usr/include/postgresql -I/usr/include/xmltok -pthread     -I/usr/include/apache2  -I/usr/include/apr-1.0   -I/usr/include/apr-1.0 -I/usr/include/postgresql -I/usr/include/mysql -I/usr/local/include/python3.2m -DNDEBUG  -c -o mod_wsgi.lo mod_wsgi.c && touch mod_wsgi.slo
mod_wsgi.c: In function 'Adapter_environ':
mod_wsgi.c:3601: warning: assignment makes pointer from integer without a cast
mod_wsgi.c: In function 'Dispatch_environ':
mod_wsgi.c:8372: warning: assignment makes pointer from integer without a cast
mod_wsgi.c: In function 'Auth_environ':
mod_wsgi.c:13375: warning: assignment makes pointer from integer without a cast
/usr/share/apr-1.0/build/libtool --silent --mode=link --tag=disable-static i486-linux-gnu-gcc -o mod_wsgi.la  -rpath /usr/lib/apache2/modules -module -avoid-version    mod_wsgi.lo -L/usr/local/lib -L/usr/local/lib/python3.2/config -lpython3.2 -lpthread -ldl -lutil -lm
/usr/bin/ld: cannot find -lpython3.2
collect2: ld returned 1 exit status
apxs:Error: Command failed with rc=65536
.
make: *** [mod_wsgi.la] Error 1

```The following python library files are located in /usr/local/lib/:
libpython3.2m.a
libpyhton3.2m.so.1.0
libpython3.2m.so -> libpyhton3.2m.so.1.0
libpyhton3.so

The folder /usr/local/lib/python3.2/config does not exist.

Thanks for your help.

---

### Post by mbouza on 2011-03-16
OK, I managed to compile mod_wsgi for Pyhton 3.2. I did the follwing:

[LIST]
[*]In Makefile, i changed *-L/usr/local/lib/python3.2/config* to *-L/usr/local/lib/python3.2/config-3.2m*
[*]In */usr/local/lib/python3.2/config-3.2m/, *I created a symbolic link libpython3.2.a -> libpython3.2m.a
[/LIST]
With this, I was able to complie mod_wsgi 3.3 for Python 3.2.

When restarting apache, I get now the following error:

```

apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/wsgi.load: Cannot load /usr/lib/apache2/modules/mod_wsgi.so into server: /usr/lib/apache2/modules/mod_wsgi.so: undefined symbol: PyCObject_FromVoidPtr

```

---


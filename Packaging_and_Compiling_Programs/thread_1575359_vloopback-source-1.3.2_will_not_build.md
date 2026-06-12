---
title: "vloopback-source-1.3.2 will not build"
date: 2010-09-15
forum: Packaging and Compiling Programs
---

### Post by marcia on 2010-09-15
Dear All,

I have ubuntu studio with the 2.6.31-9-rt kernel, 9.10 karmic. I am trying to install the vloopback module from the lucid vloopback source 1.3.2 package. I used module-assistant but got this error message:

Building vloopback driver...
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CC [M]  /usr/src/modules/vloopback/vloopback.o
/usr/src/modules/vloopback/vloopback.c: In function ‘create_pipe’:
/usr/src/modules/vloopback/vloopback.c:1323: error: implicit declaration of function ‘init_MUTEX’
make[4]: *** [/usr/src/modules/vloopback/vloopback.o] Error 1
make[3]: *** [_module_/usr/src/modules/vloopback] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make[2]: *** [vloopback] Error 2
make[2]: Leaving directory `/usr/src/modules/vloopback'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/vloopback'
make: *** [kdist_build] Error 2

Does anyone have any idea how to build this correctly?

I will appreciate any suggestions.

Thank you sincerely for your help.

Marcia

---

### Post by SevenMachines on 2010-09-16
These things should be fixed in svn, best use that
>  svn co [http://www.lavrsen.dk/svn/vloopback/trunk/](http://www.lavrsen.dk/svn/vloopback/trunk/) vloopback

---

### Post by marcia on 2010-09-16
Thank you so much for your help. I will try that and let you know.


Thanks again.

Sincerely,

Marcia

---

### Post by marcia on 2010-09-16
Thank you again. I finally installed from svn and I finally have vloopback module installed. Thank you very much.:D

Sincerely,

Marcia

---

### Post by afrodeity on 2010-11-20
I get the same error, but from subversion sources

```
 svn co http://www.lavrsen.dk/svn/vloopback/trunk/ vloopback 
```


```
make
make -C /lib/modules/2.6.37-020637rc1-generic/build SUBDIRS=/home/afrodeity/SVN/vloopback modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.37-020637rc1-generic'
  CC [M]  /home/afrodeity/SVN/vloopback/vloopback.o
/home/afrodeity/SVN/vloopback/vloopback.c: In function &#8216;create_pipe&#8217;:
/home/afrodeity/SVN/vloopback/vloopback.c:1339: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[2]: *** [/home/afrodeity/SVN/vloopback/vloopback.o] Error 1
make[1]: *** [_module_/home/afrodeity/SVN/vloopback] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.37-020637rc1-generic'
make: *** [all] Error 2

```

Is this related to the rc kernel?

---

### Post by afrodeity on 2010-12-08
I ran module-assistant, updated and prepared, but there was no vloopback option. I then succeeded in compiling the source package, so obviously the prepare option helped in some way.

---


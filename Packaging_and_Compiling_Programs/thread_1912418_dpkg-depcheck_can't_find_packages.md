---
title: "dpkg-depcheck can't find packages"
date: 2012-01-20
forum: Packaging and Compiling Programs
---

### Post by faustism on 2012-01-20
When I run ```
dpkg-depcheck -d ./configure --disable-werror --prefix=/usr/local/kLPRng --sysconfdir=/usr/local/kLPRng/etc --enable-kerberos --with-klpr_auth=k5conn --disable-setuid --disable-shared

``` on a program I am trying to create a package for, it doesn't return any needed packages, but a lot of files that it cannot find the packages for. My install of oneiric is relatively fresh, and I did not mess around with the system files, so they should be associated with a package.

The output was ```
warning: alternatives used:
/etc/ld.so.conf.d/i386-linux-gnu_GL.conf --> /usr/lib/i386-linux-gnu/mesa/ld.so.conf
The following files did not appear to belong to any package:
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/crtn.o
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/libcom_err.so
/usr/lib/libcroco-0.6.so.3
/etc/alternatives/i386-linux-gnu_gl_conf
/usr/bin/msgmerge
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/mit-krb5/libk5crypto.so
/lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
/usr/lib/gcc/i686-linux-gnu/4.6.1/libgcc.a
/etc/ld.so.conf.d/i386-linux-gnu_GL.conf
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/libkrb5.so.3.3
/lib/i386-linux-gnu/libkeyutils.so.1.3
/usr/lib/gcc/i686-linux-gnu/4.6.1/include/varargs.h
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/libk5crypto.so.3.1
/usr/bin/msgfmt
/usr/lib/gcc/i686-linux-gnu/4.6.1/libgcc_s.so
/usr/lib/gcc/i686-linux-gnu/4.6.1/include-fixed/syslimits.h
/usr/lib/libxml2.so.2
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libk5crypto.so.3.1
/usr/lib/libgettextsrc-0.18.1.so
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/libk5crypto.so
/usr/include/mit-krb5/krb5/krb5.h
/lib/i386-linux-gnu/libpcre.so.3
/usr/lib/gcc/i686-linux-gnu/4.6.1/include/float.h
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/libutil.so
/lib/i386-linux-gnu/libkeyutils.so.1
/usr/lib/libcroco-0.6.so.3.0.1
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crtn.o
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libc.so
/usr/lib/locale/locale-archive
/usr/lib/i386-linux-gnu/libkrb5support.so.0.1
/usr/lib/gcc/i686-linux-gnu/4.6.1/include/stdint.h
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crt1.o
/usr/include/et/com_err.h
/usr/lib/gcc/i686-linux-gnu/4.6.1/cc1
/usr/include/com_err.h
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/libkrb5.so
/usr/bin/xgettext
/usr/include/krb5/krb5.h
/usr/lib/gcc/i686-linux-gnu/4.6.1/include/stddef.h
/usr/lib/gcc/i686-linux-gnu/4.6.1/collect2
/usr/lib/libxml2.so.2.7.8
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libkrb5.so.3.3
/usr/lib/gcc/i686-linux-gnu/4.6.1/crtbegin.o
/usr/lib/i386-linux-gnu/libkrb5support.so.0
/etc/ld.so.conf
/usr/lib/gcc/i686-linux-gnu/4.6.1/crtend.o
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/mit-krb5/libkrb5.so
/lib/i386-linux-gnu/libglib-2.0.so.0
/usr/lib/gcc/i686-linux-gnu/4.6.1/include-fixed/limits.h
/usr/lib/libunistring.so.0
/usr/lib/libunistring.so.0.1.2
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/crt1.o
/usr/lib/libgettextlib-0.18.1.so
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crti.o
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/crti.o
/usr/include/mit-krb5/krb5.h
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/libc.so
/usr/lib/gcc/i686-linux-gnu/4.6.1/include/stdarg.h
/lib/i386-linux-gnu/libpcre.so.3.12.1
/usr/lib/i386-linux-gnu/mesa/ld.so.conf
/usr/include/krb5.h
Packages needed:
  

```

Thanks you in advance for any help. I have tried updating my package lists, but that doesn't seem to be of any help.

---

### Post by MadCow108 on 2012-01-20
my guess is that dpkg-depcheck does not deal well with the paths that are used, possibly due to multiarch
all the ../.. out of the gcc dirs and into usr/lib

I think you will have to do it manually with that output. or run the thing in maverick, lucid and see if that works (if yes its definitely multiarch related)

---

### Post by faustism on 2012-01-21
Thanks, I did it manually, but it seems like there should be a better explanation. Especially because I got matches for about a third of them just by using "dpkg -S <filename>".

---


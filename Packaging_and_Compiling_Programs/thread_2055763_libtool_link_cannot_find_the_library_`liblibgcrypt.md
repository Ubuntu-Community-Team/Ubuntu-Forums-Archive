---
title: "libtool: link: cannot find the library `/lib/libgcrypt.la'"
date: 2012-09-10
forum: Packaging and Compiling Programs
---

### Post by djeyewater on 2012-09-10
I'm trying to compile PHP, but the compile fails with the error:

```
libtool: link: cannot find the library `/lib/libgcrypt.la' or unhandled argument `/lib/libgcrypt.la'
make: *** [sapi/cli/php] Error 1
```

I have libgcrypt installed in a non-standard location, but I am specifying the location with the LDFLAGS and CPPFLAGS in configure. It is still looking in /lib for the files though, I don't why?

This is my configure line:
```
LDFLAGS=-L$HOME/apps/libgcrypt/lib CPPFLAGS=-I$HOME/apps/libgcrypt/include ./configure --prefix=$HOME/apps/$PHP \
--enable-mbstring \
--enable-zip \
--enable-fpm \
--enable-ftp \
--with-openssl=$HOME/apps/openssl \
--with-openssl-dir=$HOME/apps/openssl \
--with-jpeg-dir=$HOME/apps/libjpeg-turbo \
--with-gd \
--with-freetype-dir=/usr \
--with-gettext \
--with-xmlrpc \
--with-icu-dir=$HOME/apps/icu4c \
--enable-intl \
--with-pdo-mysql=mysqlnd \
--with-mysql=mysqlnd \
--with-mysqli=mysqlnd \
--with-zlib-dir=/usr \
--with-kerberos=/usr \
--with-png-dir=/usr \
--with-ldap=$HOME/apps/openldap \
--with-curl=$HOME/apps/curl \
--with-mcrypt=$HOME/apps/libmcrypt \
--with-mhash=$HOME/apps/mhash \
--with-tidy=$HOME/apps/tidy \
--with-libxml-dir=$HOME/apps/libxml2 \
--with-iconv-dir=$HOME/apps/libiconv \
--with-xsl=$HOME/apps/libxslt
```

I have opened this as a bug on php.net, but I'm not sure whether it is actually a bug with PHP, or I'm missing something else I need to do to make libtool look in the right place for the gcrypt lib?

Libtool version is libtool (GNU libtool) 2.4.2, PHP I'm trying to compile is 5.4.6 but I also get the same error with 5.4.3, libgcrypt version is 1.5.0.

Thanks

Dave

---

### Post by djeyewater on 2012-11-22
No-one has any ideas on this?

---

### Post by dodle on 2012-11-23
Have you tried putting LDFLAGS and CPPFLAGS to the right of the ./configure command?

---

### Post by djeyewater on 2012-11-23
Thanks for the suggestion, I have tried that now, but unfortunately still get the same result.

---

### Post by steeldriver on 2012-11-23
Do you have the libgcrypt-dev package (libgcrypt11-dev?) installed or just the runtime?

I guess libtool generates the .la file from the .a file - and that appears to only be in the dev package:

```
$ apt-file show libgcrypt11 | grep '\.so'
libgcrypt11: /lib/i386-linux-gnu/libgcrypt.so.11
libgcrypt11: /lib/i386-linux-gnu/libgcrypt.so.11.7.0
libgcrypt11-dbg: /usr/lib/debug/lib/i386-linux-gnu/libgcrypt.so.11.7.0
libgcrypt11-dbg: /usr/lib/debug/lib/libgcrypt.so.11.7.0
libgcrypt11-dev: /lib/i386-linux-gnu/libgcrypt.so
$ 
$ apt-file show libgcrypt11 | grep '\.a'
libgcrypt11-dev: /lib/i386-linux-gnu/libgcrypt.a

```

---

### Post by djeyewater on 2012-11-24
Thanks for the suggestion. I don't have root access (technically I do, but I need to get PHP built in the same way as I will have to on my webserver, where I don't have root access).

My build of libgcrypt ($HOME/apps/libgcrypt) did not have the libgcrypt.a file. I have now rebuilt it using the --enable-static=yes option, which did create the libgcrypt.a file.

However, I still get the same error when trying to build PHP.

Other things I have tried are:
```
export LD_RUN_PATH="$HOME/apps/libgcrypt/lib:$LD_LIBRARY_PATH"
export LD_PRELOAD="$HOME/apps/libgcrypt/lib/libgcrypt.so:$LD_PRELOAD"
export LD_LIBRARY_PATH="$HOME/apps/libgcrypt/lib:$LD_LIBRARY_PATH"
ENV="-L $HOME/apps/libgcrypt/lib" CFLAGS="-Wl,--rpath -Wl,$HOME/apps/libgcrypt/lib" LDFLAGS=-L$HOME/apps/libgcrypt/lib CPPFLAGS=-I$HOME/apps/libgcrypt/include ./configure
```

But I still always get the same error,
```
libtool: link: cannot find the library `/lib/libgcrypt.la' or unhandled argument `/lib/libgcrypt.la'
make: *** [sapi/cli/php] Error 1
```

---

### Post by steeldriver on 2012-11-24
Sorry I don't know what else to suggest - it's odd that it appears to be looking in /lib regardless

I'm confused about the relationship between mcrypt and gcrypt though - is gcrypt supposed to be a drop in replacement for mcrypt? if so what exactly is 

```
--with-mcrypt=$HOME/apps/lib**m**crypt \
```

pointing to? should that be where you put your local lib**g**crypt path? or are they different things?

---

### Post by djeyewater on 2012-11-24
I think gcrypt and mcrypt are both different. From what I understand, mcrypt is an additional option for PHP. While I think gcrypt is probably needed for SSL support.

I did try building with various options before I made the original post in this thread, but I can't remember what the results were now. I will try again to check whether it's SSL support that's requiring gcrypt when I get a minute.

---

### Post by djeyewater on 2012-11-27
So, I ran ./configure followed by make a lot different times with different configuration options in an attempt to narrow down what was causing the error. This took quite a long time as the error only comes up quite a way through the make process.

Eventually I found that PHP would build okay without --with-xsl=$HOME/apps/libxslt. Sure enough, if I check $HOME/apps/libxslt/lib/libexslt.la, I have the following line:
```
# Libraries that this one depends upon.
dependency_libs=' /lib/libgcrypt.la /home/djeyewater/apps/libxslt/lib/libxslt.la -L/home/djeyewater/apps/libxml2/lib /home/djeyewater/apps/libxml2/lib/libxml2.la -ldl -lz -lm'
```

My guess is that when I built libxslt, Ubuntu included /lib/libgcrypt.la. But in an update this file must have been removed.

Rebuilding libxslt pointing it at my libgcrypt installation solved the problem, and I can now install PHP okay. If anyone else has the same issue, this is the configure command for libxslt that worked for me (I'm not sure if the LD_LIBRARY_PATH and CPPFLAGS values are actually needed):
```
export LD_LIBRARY_PATH="$HOME/apps/libgcrypt/lib:$LD_LIBRARY_PATH"
LDFLAGS=-L$HOME/apps/libgcrypt/lib CPPFLAGS=-I$HOME/apps/libgcrypt/include ./configure --prefix=$HOME/apps/$LIBXSLT --with-libxml-prefix=$HOME/apps/libxml2
```

Thanks for the help and suggestions.

Dave

---


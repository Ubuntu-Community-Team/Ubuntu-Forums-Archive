---
title: ": /usr/local/lib/libsasl2.so.2: no version information available"
date: 2008-09-03
forum: Programming Talk
---

### Post by lexarrow on 2008-09-03
Hi all,

I'm working on a script that downloads, installs and configures applications on a Hardy 8.04.1 i686 server.

I compiled Cyrus SASL 2.2 from source with no errors and after compiling openLDAP, when it starts, I get:
```
 /usr/local/lib/libsasl2.so.2: no version information available (required by /usr/local/libexec/slapd)
info: /etc/init.d/slapd: LDAP properly started
```
LDAP works, but without tls support

The cause of the problem I think it is that libsasl2-2, libsasl2-2-modules, and libsasl2-2-dev are already installed by default in Ubuntu and cannot be removed because lots of other packages depend on them

The ./configure I used for ldap:
```
env CPPFLAGS="-DUSE_SASL_AUTH -DUSE_CYRUS_SASL -I/usr/local/include" LIBS="-L/usr/local/lib -lsasl" ./configure --libdir=/usr/local/lib/ldap --includedir=/usr/local/include/ldap --with-cyrus-sasl --build=i686-pc-linux-gnu --host=i686-pc-linux-gnu --target=i686-pc-linux-gnu --enable-crypt --enable-modules --enable-perl --enable-accesslog --enable-syslog --with-tls=openssl --enable-monitor --enable-hdb --enable-dependency
```

Any help would be much appreciated!

---

### Post by charasoverride on 2008-09-30
I got the same problem:
```

$:/etc/apache2/sites-enabled# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                   
/usr/sbin/apache2: /usr/local/lib/libsasl2.so.2: no version information available (required by /usr/lib/libldap_r-2.4.so.2)
Syntax error on line 1 of /etc/apache2/sites-enabled/cacert.pem:
Invalid command '-----BEGIN', perhaps misspelled or defined by a module not included in the server configuration
                                                                                                                                      [fail]

```
When starting anything which depends on this module i get the error. At this point i cannot event start apache.. Any clue on this?

---

### Post by charasoverride on 2008-09-30
SOLVED !!.. SOLUTION:

I did a 
```
$ ldconfig -p | grep libsasl2
``` and the library path was pointing to /usr/local/lib.. i needed it to be /usr/lib so i modified the file: /etc/ld.so.conf.d/libc.conf
```

$ nano /etc/ld.so.conf.d/libc.conf

```
i commented /usr/local/lib and added /usr/lib:
```

# libc default configuration
#/usr/local/lib
/usr/lib

```
Then run :
```

/sbin/ldconfig -v

``` to set up the correct links for the shared binaries and rebuild  the cache.

After this i did not get the error anymore.

cheers

---

### Post by charasoverride on 2008-09-30
SOLVED !!.. SOLUTION:

I did a 
```
$ ldconfig -p | grep libsasl2
``` and the library path was pointing to /usr/local/lib.. i needed it to be /usr/lib so i modified the file: /etc/ld.so.conf.d/libc.conf
```

$ nano /etc/ld.so.conf.d/libc.conf

```
i commented /usr/local/lib and added /usr/lib:
```

# libc default configuration
#/usr/local/lib
/usr/lib

```
Then run :
```

/sbin/ldconfig -v

``` to set up the correct links for the shared binaries and rebuild  the cache.

After this i did not get the error anymore.

cheers

---

### Post by charasoverride on 2008-10-01
From my side the thread can be marked as solved!

---

### Post by &#27969;&#27801;&#26539; on 2009-06-04
> **charasoverride said:**
> SOLVED !!.. SOLUTION:
 
I did a 
```
$ ldconfig -p | grep libsasl2
``` and the library path was pointing to /usr/local/lib.. i needed it to be /usr/lib so i modified the file: /etc/ld.so.conf.d/libc.conf
```

$ nano /etc/ld.so.conf.d/libc.conf

```
i commented /usr/local/lib and added /usr/lib:
```

# libc default configuration
#/usr/local/lib
/usr/lib

```
Then run :
```

/sbin/ldconfig -v

``` to set up the correct links for the shared binaries and rebuild the cache.
 
After this i did not get the error anymore.
 
cheers
 
 
thanks

---

### Post by fuxximus on 2010-12-02
i'm a complete newbie, plus i'm very lazy, but thank you very much for this info.
I, usually, just read on and use the information found on forums through google. Regarding ubuntu i keep coming back here through google /obviously/, but I have never thought I'd register to say thank you. 

so thank you. even though i'm not sure whether first few steps were necessary for me, but the whole thing worked no problems yet. i just don't know what i did exactly, what the commands mean, i probably won't be diggin in to find out :P. 

 again thank you

---


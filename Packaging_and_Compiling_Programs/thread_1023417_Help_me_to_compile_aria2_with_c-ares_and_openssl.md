---
title: "Help me to compile aria2 with c-ares and openssl"
date: 2008-12-27
forum: Packaging and Compiling Programs
---

### Post by SuperBo on 2008-12-27
I downloaded aria2-1.1.1 and compile it

```
./configure --prefix=/usr --enable-metalink --enable-epoll  --enable-threads=win32  --enable-threads=posix --enable-largefile --with-gnutls --with-libxml2 --with-sqlite3 --with-libcares --with-openssl

```
Although I have installed libares-dev and openssl but the resutl is

```
Build:          i686-pc-linux-gnu
Target:         i686-pc-linux-gnu
Install prefix: /usr
CFLAGS:         -g -O2
CPPFLAGS:       
LDFLAGS:        
LIBS:           
SQLite3:        yes
GnuTLS:         yes
OpenSSL:        
CA Bundle:      
LibXML2:        yes
LibExpat:       
LibCares:       
Libz:           yes
Bittorrent:     yes
Metalink:       yes

```

What should I do to enable all featrues?

---

### Post by maddog39 on 2008-12-27
Umm there are duplicate libraries in there which it lets you use. GnuTLS and OpenSSL are both SSL libraries, the configure script chose to use GnuTLS. Also, Expat and XML2 are both XML libraries and one is found and was chosen by the configure script. To enable cares support you need to install the libc-ares-dev package from the repository.

sudo apt-get install libc-ares-dev or install view synaptic.

---

### Post by SuperBo on 2008-12-27
> **maddog39 said:**
> Umm there are duplicate libraries in there which it lets you use. GnuTLS and OpenSSL are both SSL libraries, the configure script chose to use GnuTLS. Also, Expat and XML2 are both XML libraries and one is found and was chosen by the configure script. To enable cares support you need to install the libc-ares-dev package from the repository.

sudo apt-get install libc-ares-dev or install view synaptic.

Thank you very much.
It works

---


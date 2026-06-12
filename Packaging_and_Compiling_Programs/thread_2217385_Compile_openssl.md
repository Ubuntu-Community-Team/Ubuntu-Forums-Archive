---
title: "Compile openssl"
date: 2014-04-17
forum: Packaging and Compiling Programs
---

### Post by keziaha on 2014-04-17
when i compile openssl-1.0.1e and i see symbol object (readelf -s libssl.so.1.0.0), i have :

 777: 00042dc0   401 FUNC    GLOBAL DEFAULT   11 SSL_SESSION_free
 1119: 0003dbb0   493 FUNC    GLOBAL DEFAULT   11 SSL_CTX_free
   513: 000403f0   619 FUNC    GLOBAL DEFAULT   11 SSL_free

In version ubuntu 13.04, i have 

   499: 000379f0   401 FUNC    GLOBAL DEFAULT   12 SSL_SESSION_free@@OPENSSL_1.0.0
   530: 00032ed0   397 FUNC    GLOBAL DEFAULT   12 SSL_CTX_free@@OPENSSL_1.0.0
   625: 00035640   619 FUNC    GLOBAL DEFAULT   12 SSL_free@@OPENSSL_1.0.0

why there are suffix "@@OPENSSL_1.0.0" in symbol name of fonction ?

---

### Post by oldos2er on 2014-04-19
Moved to Packaging & Compiling Programs.

---


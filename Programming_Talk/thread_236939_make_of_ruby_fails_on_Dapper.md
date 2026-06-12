---
title: "make of ruby fails on Dapper"
date: 2006-08-15
forum: Programming Talk
---

### Post by jeet on 2006-08-15
I recently upgraded my Ubuntu to Dapper. I am trying to compile ruby on it. After running configure I edit the ext/Setup file and uncomment the following lines:

digest
digest/md5
openssl
readline
stringio
zlib


 and then I run make which fails with following message

> SETUP=ext/Setup
EXTOBJS=ext/extinit.o ext/digest/digest.a ext/digest/md5/md5.a ext/openssl/openssl.a ext/stringio/stringio.a ext/zlib/zlib.a
EXTLIBS=-lssl -lcrypto -lz
making ruby
make[1]: Entering directory `/home/navjeet/ruby-1.8.4'
gcc -g -O2  -DRUBY_EXPORT   -rdynamic -Wl,-export-dynamic -L.   main.o ext/extinit.o ext/digest/digest.a ext/digest/md5/md5.a ext/openssl/openssl.a ext/stringio/stringio.a ext/zlib/zlib.a -lruby-static -ldl -lcrypt -lm  -lssl -lcrypto -lz -o ruby
ext/digest/md5/md5.a(md5init.o):(.data.rel+0x8): undefined reference to `rb_Digest_MD5_Init'
ext/digest/md5/md5.a(md5init.o):(.data.rel+0xc): undefined reference to `rb_Digest_MD5_Update'
ext/digest/md5/md5.a(md5init.o):(.data.rel+0x10): undefined reference to `rb_Digest_MD5_End'
ext/digest/md5/md5.a(md5init.o):(.data.rel+0x14): undefined reference to `rb_Digest_MD5_Final'
ext/digest/md5/md5.a(md5init.o):(.data.rel+0x18): undefined reference to `rb_Digest_MD5_Equal'
collect2: ld returned 1 exit status
make[1]: *** [ruby] Error 1
make[1]: Leaving directory `/home/navjeet/ruby-1.8.4'
make: *** [all] Error 2

What is source of this error? Do you think I may not have some library installed ?

---


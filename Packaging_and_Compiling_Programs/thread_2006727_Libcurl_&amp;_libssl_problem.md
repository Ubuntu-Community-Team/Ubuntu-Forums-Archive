---
title: "Libcurl &amp; libssl problem"
date: 2012-06-19
forum: Packaging and Compiling Programs
---

### Post by nradtke on 2012-06-19
I'm writing a C++ program that uses libcurl to connect to a website and get some information.  When I made the first version that only used regular http, it works fine.  I tried adding ssl to it so I can connect to https sites and now I'm getting this error when I try to run the program:

Error=/usr/lib/x86_64-linux-gnu/libcurl.so.4: symbol SSL_CTX_set_srp_password, version OPENSSL_1.0.1 not defined in file libssl.so.1.0.0 with link time reference.

I'm running 12.04 with all updates as of June 19, 2012.  Does this mean anything to anyone?  I've installed the libcurl4-openssl-dev package.

---


---
title: "autobuilder fails to build openssl 1.0.0d-2ubuntu2~lucid1 i386"
date: 2011-09-01
forum: Packaging and Compiling Programs
---

### Post by ptn107 on 2011-09-01
I don't get it.  It builds for amd64 but not i386.  Here's the error:
```
dpkg-gensymbols: warning: some libraries disappeared in the symbols file: libssl.so.1.0.0 libcrypto.so.1.0.0
Use of uninitialized value $_[0] in sprintf at /usr/share/perl5/Dpkg/ErrorHandling.pm line 48.
dpkg-gensymbols: warning:  doesn't match completely debian/libssl1.0.0.symbols
--- debian/libssl1.0.0.symbols (libssl1.0.0_1.0.0d-2ubuntu2~lucid1_i386)
+++ dpkg-gensymbolsEMiYDe	2011-09-01 04:40:48.000000000 +0000
@@ -1,4 +0,0 @@
-libcrypto.so.1.0.0 libssl1.0.0 #MINVER#
- (symver|optional)OPENSSL_1.0.0 1.0.0
-libssl.so.1.0.0 libssl1.0.0 #MINVER#
- (symver|optional)OPENSSL_1.0.0 1.0.0
make: *** [binary-arch] Error 3
dpkg-buildpackage: error: /usr/bin/fakeroot debian/rules binary gave error exit status 2
```

The full build log is here: [_http://paste.ubuntu.com/679388/_]("http://paste.ubuntu.com/679388/")

---

### Post by ptn107 on 2011-09-02
bump

---


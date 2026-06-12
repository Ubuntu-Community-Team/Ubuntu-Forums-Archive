---
title: "Trouble with Qmail"
date: 2007-04-25
forum: Packaging and Compiling Programs
---

### Post by @ndreX! on 2007-04-25
I got a problem when i trying  to compile Qmail... I don't know if it's a problem of my libraries, or what.

This is the Error:

```
./compile qmail-remote.c
qmail-remote.c:36:25: error: openssl/ssl.h: No such file or directory
qmail-remote.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
qmail-remote.c: In function ‘ssl_timeoutread’:
qmail-remote.c:132: error: ‘ssl’ undeclared (first use in this function)
qmail-remote.c:132: error: (Each undeclared identifier is reported only once
qmail-remote.c:132: error: for each function it appears in.)
qmail-remote.c:134: error: ‘SSL_ERROR_WANT_READ’ undeclared (first use in this function)
qmail-remote.c:135: error: ‘SSL_ERROR_NONE’ undeclared (first use in this function)
qmail-remote.c: In function ‘ssl_timeoutwrite’:
qmail-remote.c:157: error: ‘ssl’ undeclared (first use in this function)
qmail-remote.c:159: error: ‘SSL_ERROR_WANT_WRITE’ undeclared (first use in this function)
qmail-remote.c:160: error: ‘SSL_ERROR_NONE’ undeclared (first use in this function)
qmail-remote.c: At top level:
qmail-remote.c:177: error: expected ‘)’ before ‘*’ token
qmail-remote.c:183: error: expected declaration specifiers or ‘...’ before ‘X509_STORE_CTX’
qmail-remote.c: In function ‘smtp’:
qmail-remote.c:346: error: ‘SSL_CTX’ undeclared (first use in this function)
qmail-remote.c:346: error: ‘ctx’ undeclared (first use in this function)
qmail-remote.c:400: error: ‘ssl’ undeclared (first use in this function)
qmail-remote.c:404: error: ‘SSL_FILETYPE_PEM’ undeclared (first use in this function)
qmail-remote.c:409: error: ‘client_cert_cb’ undeclared (first use in this function)
qmail-remote.c:418: error: ‘SSL_VERIFY_PEER’ undeclared (first use in this function)
qmail-remote.c:454: error: ‘X509_V_OK’ undeclared (first use in this function)
qmail-remote.c:462: error: ‘NID_commonName’ undeclared (first use in this function)
qmail-remote.c: In function ‘main’:
qmail-remote.c:590: warning: return type of ‘main’ is not ‘int’
make: *** [qmail-remote.o] Error 1

```

Well i hope your help.

Regards.
@ndreX!

---

### Post by WW on 2007-04-25
Install the package **libssl-dev**, e.g.
```

sudo apt-get install libssl-dev

```

---

### Post by @ndreX! on 2007-04-25
Thanks, that's work for one of these packages.

Now triying to compile another package (ever of qmail), i got this:

```

./load tcpserver rules.o remoteinfo.o timeoutconn.o cdb.a \
        dns.a time.a unix.a byte.a  `cat socket.lib`
/usr/bin/ld: errno: TLS definition in /lib/libc.so.6 section .tbss mismatches non-TLS reference in tcpserver.o
/lib/libc.so.6: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [tcpserver] Error 1

```

Well, i've try to install libc (i dont know if that's the problem) i got this another error:

```

Package libc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libc has no installation candidate

```

Some idea?

Thanks.
@ndreX!

---

### Post by derbouka on 2007-10-09
> **@ndreX! said:**
> Thanks, that's work for one of these packages.

Now triying to compile another package (ever of qmail), i got this:

```

./load tcpserver rules.o remoteinfo.o timeoutconn.o cdb.a \
        dns.a time.a unix.a byte.a  `cat socket.lib`
/usr/bin/ld: errno: TLS definition in /lib/libc.so.6 section .tbss mismatches non-TLS reference in tcpserver.o
/lib/libc.so.6: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [tcpserver] Error 1

```
 You can solve that problem by editing the file "error.h" and removing the line "extern int errno;" and put there "#include <errno.h>"

---


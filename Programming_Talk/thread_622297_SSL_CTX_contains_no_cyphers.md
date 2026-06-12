---
title: "SSL CTX contains no cyphers"
date: 2007-11-24
forum: Programming Talk
---

### Post by JimBodkins on 2007-11-24
I have been using CentOS 4.5 and was looking at Ubuntu as a new platform.

I just compiled and ran one ap - a hotel reservation module - and received - SSL CTX contains no ciphers.

I guess this means ubuntu cant be used commercially. Very disappointing.



P.S.
ERR_print_errors_fp (logfd); generates

18452:error:140A90A1:SSL routines:SSL_CTX_new:library has no ciphers:ssl_lib.c:1
424:

This is in a function that does ..

{
  SSL_METHOD *method;
  SSL_CTX *ctx;

  OpenSSL_add_all_algorithms ();        /* Load cryptos, et.al. */
  SSL_load_error_strings ();    /* Bring in and register error messages */
  method = SSLv3_client_method ();      /* Create new client-method instance */
  ctx = SSL_CTX_new (method);   /* Create new context */
  if (ctx == NULL)
    {
      ERR_print_errors_fR_print_errors_fp (logfd);
      abort ();
    }
  return ctx;

---

### Post by kadamcd on 2008-08-29
It is the bug in openssl lib
see here [Bug#335836]("http://lists.alioth.debian.org/pipermail/pkg-openssl-devel/2005-October/000219.html")

Solution for your problem is, call the routine SSL_library_init()
before making call to any SSL library functions.

It works!!!
\\:D/

---

### Post by nvteighen on 2008-08-29
It's a bug that affects Debian-based distributions, including Debian itself. CentOS is RedHat-based, so you were safe there... :)

---

### Post by gajanan.khandake on 2008-08-29
Thank's kadamcd....
it worked for me too
:)

---

### Post by gmanipon on 2012-11-26
kadamcd's solution also works for Ubuntu 12.04.

---


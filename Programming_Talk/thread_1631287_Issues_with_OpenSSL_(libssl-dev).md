---
title: "Issues with OpenSSL (libssl-dev)"
date: 2010-11-26
forum: Programming Talk
---

### Post by igfud on 2010-11-26
To make a long story short - I am trying to add SSL to a chat server and client I wrote.  I installed the openssl-dev library from the repos and all of the SSL libraries (ssl.h, bio.h, err.h, etc.) are located in /usr/include/openssl.

I am able to declare instances of the SSL_CTX object as long as ssl.h is included, but calling any functions results in an "undefined reference to `*function name*'".

I am following [this IBM tutorial]("http://www.ibm.com/developerworks/linux/library/l-openssl.html") on setting up SSL.  Below I've given a simple test program and the output from gcc.  Ideas?

Thanks,
igfud

```
/* OpenSSL headers */

#include "openssl/bio.h"
#include "openssl/ssl.h"
#include "openssl/err.h"

int main()
{
	SSL_CTX testCTX;
	
	/* Initializing OpenSSL */

	SSL_load_error_strings();
	ERR_load_BIO_strings();
	OpenSSL_add_all_algorithms();
	
	return 0;
}
```

```
igfud@igfud-laptop:~/Documents/csci4273/pa4$ gcc -o ssltest ssltest.c 
/tmp/ccMu9Tmh.o: In function `main':
ssltest.c:(.text+0x20): undefined reference to `SSL_load_error_strings'
ssltest.c:(.text+0x25): undefined reference to `ERR_load_BIO_strings'
ssltest.c:(.text+0x2a): undefined reference to `OPENSSL_add_all_algorithms_noconf'
```

---

### Post by Arndt on 2010-11-26
> **igfud said:**
> To make a long story short - I am trying to add SSL to a chat server and client I wrote.  I installed the openssl-dev library from the repos and all of the SSL libraries (ssl.h, bio.h, err.h, etc.) are located in /usr/include/openssl.

I am able to declare instances of the SSL_CTX object as long as ssl.h is included, but calling any functions results in an "undefined reference to `*function name*'".

I am following [this IBM tutorial]("http://www.ibm.com/developerworks/linux/library/l-openssl.html") on setting up SSL.  Below I've given a simple test program and the output from gcc.  Ideas?

Thanks,
igfud

```
/* OpenSSL headers */

#include "openssl/bio.h"
#include "openssl/ssl.h"
#include "openssl/err.h"

int main()
{
	SSL_CTX testCTX;
	
	/* Initializing OpenSSL */

	SSL_load_error_strings();
	ERR_load_BIO_strings();
	OpenSSL_add_all_algorithms();
	
	return 0;
}
```

```
igfud@igfud-laptop:~/Documents/csci4273/pa4$ gcc -o ssltest ssltest.c 
/tmp/ccMu9Tmh.o: In function `main':
ssltest.c:(.text+0x20): undefined reference to `SSL_load_error_strings'
ssltest.c:(.text+0x25): undefined reference to `ERR_load_BIO_strings'
ssltest.c:(.text+0x2a): undefined reference to `OPENSSL_add_all_algorithms_noconf'
```

You have to tell gcc where those functions are. Something like -lopenssl.

---

### Post by igfud on 2010-11-26
-lssl does the trick. Hah wish they had put that one in the tutorial.  Thanks a bunch!

igfud

---


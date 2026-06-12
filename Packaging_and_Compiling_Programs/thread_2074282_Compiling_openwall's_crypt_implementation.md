---
title: "Compiling openwall's crypt implementation"
date: 2012-10-21
forum: Packaging and Compiling Programs
---

### Post by Japheth on 2012-10-21
I've been trying to use openwall's crypt implementation in my c++ programs. I downloaded the source from [http://www.openwall.com/crypt/](http://www.openwall.com/crypt/) and put it into the crypt_blowfish-1.2 directory in my home directory. The .cpp file I'm trying to compile is also in that directory. I'm getting the error listed below and I'm not sure how to fix it. I suspect I need to include a library, but I'm not sure which one.

crypttest.cpp (my program):
```

#include "crypt_blowfish-1.2/ow-crypt.h"

int main(int argc, char* argv[])
{
  return 0;
}

```

command I use to compile it:
```

 c++ crypt_blowfish-1.2/wrapper.c crypt_blowfish-1.2/crypt_blowfish.c crypt_blowfish-1.2/crypt_gensalt.c crypttest.cpp -o crypttest

```

The output:
```

/tmp/ccJo43pD.o: In function `BF_crypt(char const*, char const*, char*, int, unsigned int)':
crypt_blowfish.c:(.text+0x23e0): undefined reference to `_BF_body_r(BF_ctx*)'
collect2: ld returned 1 exit status

```

---

### Post by Japheth on 2012-10-22
I solved this. The missing function was in x86.S, which was in the downloaded source.

After messing around with the c++ compiler for a while, I realized that the makefile in the download uses gcc to compile the various c files and the .S file into .o files and I should just pass those .o files as arguments to my c++ compiler. After that, it all worked. The new command I used was:

```
c++ crypt_blowfish-1.2/x86.o crypt_blowfish-1.2/wrapper.o crypt_blowfish-1.2/crypt_blowfish.o crypt_blowfish-1.2/crypt_gensalt.o ssltest.cpp -o ssltest -lboost_system-mt -lpthread -lssl
```

---

